---
connections:
  - "[[Informatica]]"
---
```php
<?php
// Controllo se il form è stato inviato con metodo POST
if ($_SERVER['REQUEST_METHOD'] === 'POST') {

    // Raccogliamo i dati del form HTML
    $array = array(
        'name' => $_POST['name'] ?? '',     // nome dell’utente
        'email' => $_POST['email'] ?? '',   // email dell’utente
        'pass' => $_POST['pass'] ?? ''      // password inserita
    );

    // Parametri della connessione al database
    $host = "localhost";      // indirizzo del server MySQL
    $dbname = "test";         // nome del database
    $username = "root";       // utente del database
    $password = "";           // password (spesso vuota in locale)

    // Connessione al database con PDO
    try {
        $pdo = new PDO("mysql:host=$host;dbname=$dbname", $username, $password);
        $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION); // gestione errori con eccezioni
    } catch (PDOException $e) {
        die("Errore di connessione: " . $e->getMessage()); // messaggio in caso di errore
    }

    // Creo la tabella "users" se non esiste già
    $sql = "CREATE TABLE IF NOT EXISTS users (
        id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
        name VARCHAR(30) NOT NULL,
        email VARCHAR(50),
        pass VARCHAR(255) NOT NULL
    )";
    $pdo->exec($sql); // eseguo la query di creazione tabella

    // Cifro la password con password_hash
    $hashed_pass = password_hash($array['pass'], PASSWORD_DEFAULT);

    // Preparo la query SQL con i segnaposto
    $sql = "INSERT INTO users (name, email, pass) VALUES (:name, :email, :pass)";
    $stmt = $pdo->prepare($sql); // preparo la query

    // Associo i valori dell’utente ai parametri
    $stmt->bindParam(':name', $array['name']);
    $stmt->bindParam(':email', $array['email']);
    $stmt->bindParam(':pass', $hashed_pass);

    // Eseguo l’inserimento
    $stmt->execute();

    // Messaggio di conferma
    $messaggio = "Utente inserito correttamente!";
}
?>

<!-- HTML: form per invio dati -->
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <title>Registrazione Utente</title>
</head>
<body>
    <h2>Inserisci un nuovo utente</h2>

    <!-- Messaggio di conferma -->
    <?php if (isset($messaggio)): ?>
        <p style="color:green"><?= htmlspecialchars($messaggio) ?></p>
    <?php endif; ?>

    <!-- Modulo HTML -->
    <form action="index.php" method="post" style="display: flex; flex-direction: column; max-width: 300px;">
        <input type="text" name="name" placeholder="Nome Completo" required>
        <input type="email" name="email" placeholder="Email" required>
        <input type="password" name="pass" placeholder="Password" required>
        <input type="submit" value="Invia">
    </form>
</body>
</html>

```
