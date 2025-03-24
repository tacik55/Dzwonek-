<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tabela z przyciskami do edytowania</title>
    <style>
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            border: 1px solid black;
            text-align: center;
            padding: 10px;
        }
        .button-container {
            text-align: center;
            margin-top: 10px;
        }
        .add-button, .delete-button {
            margin: 5px;
            padding: 5px 10px;
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 5px;
        }
        .add-button {
            background-color: #4CAF50;
        }
        .add-button:hover {
            background-color: #45a049;
        }
        .delete-button {
            background-color: #f44336;
        }
        .delete-button:hover {
            background-color: #e53935;
        }
    </style>
</head>
<body>

    <table id="myTable">
        <thead>
            <tr>
                <th>Poniedziałek</th>
                <th>Wtorek</th>
                <th>Środa</th>
                <th>Czwartek</th>
                <th>Piątek</th>
            </tr>
        </thead>
        <tbody>
            <!-- 12 pustych wierszy -->
            <tr><td></td><td></td><td></td><td></td><td></td></tr>
            <tr><td></td><td></td><td></td><td></td><td></td></tr>
            <tr><td></td><td></td><td></td><td></td><td></td></tr>
            <tr><td></td><td></td><td></td><td></td><td></td></tr>
            <tr><td></td><td></td><td></td><td></td><td></td></tr>
            <tr><td></td><td></td><td></td><td></td><td></td></tr>
            <tr><td></td><td></td><td></td><td></td><td></td></tr>
            <tr><td></td><td></td><td></td><td></td><td></td></tr>
            <tr><td></td><td></td><td></td><td></td><td></td></tr>
            <tr><td></td><td></td><td></td><td></td><td></td></tr>
            <tr><td></td><td></td><td></td><td></td><td></td></tr>
            <tr><td></td><td></td><td></td><td></td><td></td></tr>
        </tbody>
    </table>

    <div class="button-container">
        <button class="add-button" onclick="setAction('add')">Dodaj zawartość</button>
        <button class="delete-button" onclick="setAction('delete')">Usuń zawartość</button>
    </div>

    <script>
        let currentAction = null;

        // Funkcja, która ustawia tryb akcji (dodawanie lub usuwanie)
        function setAction(action) {
            currentAction = action;
            if (action === 'add') {
                alert("Kliknij na komórkę, aby dodać zawartość.");
            } else if (action === 'delete') {
                alert("Kliknij na komórkę, aby usunąć zawartość.");
            }
        }

        // Funkcja, która wykonuje odpowiednią akcję (dodawanie lub usuwanie)
        function modifyCell(event) {
            const cell = event.target;
            
            // Jeśli akcja to 'add', dodajemy zawartość
            if (currentAction === 'add') {
                const inputText = prompt("Wpisz tekst do dodania:");
                if (inputText !== null && inputText !== "") {
                    cell.innerHTML = inputText;
                }
            }
            // Jeśli akcja to 'delete', usuwamy zawartość
            else if (currentAction === 'delete') {
                cell.innerHTML = "";
            }
        }

        // Ustawienie nasłuchiwania na kliknięcia w komórki
        const table = document.getElementById("myTable");
        table.addEventListener('click', function(event) {
            if (event.target.tagName === 'TD') {
                modifyCell(event);
            }
        });
    </script>

</body>
</html>
