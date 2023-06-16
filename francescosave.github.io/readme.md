## Questo è il pseudocodice eleborato durante la codewars Help the bookseller!.


Il codice è stato inserito all'interno di una funzione.
```js
function stockList(listOfArt, listOfCat){

  // ... the code is here

}
```

Alla funzione a titolo di esempio o test possono essere passate queste liste.

```js

let b,c

//  first sample test
b = ["BBAR 150", "CDXE 515", "BKWR 250", "BTSQ 890", "DRTY 600"]
c = ["A", "B", "C", "D"]
//  res = "(A : 0) - (B : 1290) - (C : 515) - (D : 600)"


//  second sample test
//  b = ["ABAR 200", "CDXE 500", "BKWR 250", "BTSQ 890", "DRTY 600"]
//  c = ["A", "B"]
//  res = "(A : 200) - (B : 1140)"

```

1. **Passaggio1**

    Creare un oggetto vuoto di supporto `total_books_by_category`.Con un ciclo sulla lista `listOfCat` aggiungere le `category` (key) con la `quantity` (value) inizializzata a zero.

    ```js
      let total_books_by_category = {};

      // create the zero quantity initialized support object.
      for (const category of listOfCat) {
        // set quantity of 0
        total_books_by_category[category] = 0;
  
      }

    ```

2. **Passaggio2**

    1. Ciclare la lista `listOfArt`.Prendere il `book_element` corrente della lista `listOfArt`.

    2. Estratte la categoria `book_category` del book corrente estrapolando il singolo carattere che corrisponde all'indice zero (primo carattere) dell'elemento `book_element` della lista `listOfArt`

    3. Controllare se l'oggetto `total_books_by_category` con chiave `book_category` non restituisce `undefined`,quindi esiste.In tal caso estrapola la parte destra (indice 1) dello split(con separatore spazio) dell'elemento corrente del `book_element`.Nell estrapolarlo viene convertito da stringa a numero per poter permettere la somma numerica.Valorizzare incrementando (somma il valore attuale + la quantity) il valore dell'oggetto con la quantity.


    ```js

     for (const book_element of listOfArt) {
        //  books_element in any string elemnt of array sample 
        //  ["BBAR 150", "CDXE 515", "BKWR 250", "BTSQ 890", "DRTY 600"]
        book_category = book_element[0];
        // undefined se la categoriy non esiste
        if (total_books_by_category[book_category] != undefined){
            const quantity = parseInt(book_element.split(' ')[1]);
            total_books_by_category[book_category] += quantity;
            
        }   
    }
    ```

3. **Passaggio3**

    Ripetere il passaggio2 per tutti gli elementi book della lista.il ciclo terminerà quando sara analizzato l'ultimo elemento della lista listOfArt`

4. **Passaggio4**
  
    Ritornare alla funzione l'oggetto `total_books_by_category`

    ```js
      return total_books_by_category;
    ```

5. **Passaggio5**

    Quando si uscira dalla funzione verra manadato a schermo il ritorno della funzione

      ```ps
        C:\Users\Francesco\Desktop\PairProgrammingBookSeller> node .\index.js
        { A: 0, B: 1290, C: 515, D: 600 }
      ```
