

# Introducción
Las estructuras de datos son una parte fundamental de la programación, ya que nos permiten organizar y gestionar datos de manera eficiente. Una de las estructuras de datos más importantes es la lista enlazada. En una lista enlazada, cada elemento (nodo) contiene un valor y una referencia (enlace) al siguiente nodo de la lista. Esto permite una inserción y eliminación eficientes en cualquier posición de la lista. En este ejemplo, vamos a crear una implementación de lista enlazada en JavaScript que incluye métodos para agregar, eliminar e insertar nodos, así como para imprimir la lista.

## Conceptos Básicos de las Listas Ligadas:

- Nodo: Cada elemento de la lista. Contiene:

- Valor: El dato almacenado en el nodo.

- Enlace: Una referencia al siguiente nodo de la lista.

- Cabeza (Head): El primer nodo de la lista. Si la lista está vacía, la cabeza es null.

- Cola (Tail): El último nodo de la lista. Su enlace es null.

### NOTA: este proyecto esta basado en la siguientes metodos;


- Clase Node: Define un nodo con un valor (value) y una referencia (next) que inicialmente es null.

````javascript
class LinkedList {
    constructor() {
        this.head = null;
        this.size = 0;
    }

``````

- Clase LinkedList: Define la lista enlazada con una cabeza (head) que inicialmente es null y un tamaño (size) que comienza en 0.

````javascript
isEmpty() {
    return this.size === 0;
}

getSize() {
    return this.size;
}
`````

- isEmpty y getSize: Devuelven si la lista está vacía y el tamaño de la lista, respectivamente.

````javascript
prepend(value) {
    const node = new Node(value);

    if (this.isEmpty()) {
        this.head = node;
    } else {
        node.next = this.head;
        this.head = node;
    }
    this.size++;
}
````
 - prepend: Agrega un nodo al principio de la lista. Si la lista está vacía, el nuevo nodo se convierte en la cabeza. De lo contrario, el nuevo nodo apunta al nodo actual de la cabeza y se convierte en la nueva cabeza.

````javascript
append(value) {
    const node = new Node(value);

    if (this.isEmpty()) {
        this.head = node;
    } else {
        let current = this.head;
        while (current.next) {
            current = current.next;
        }
        current.next = node;
    }
    this.size++;
}
````
-  append: Agrega un nodo al final de la lista. Si la lista está vacía, el nuevo nodo se convierte en la cabeza. De lo contrario, recorre la lista hasta el último nodo y asigna el nuevo nodo como el siguiente nodo del último.

````javascript
insert(value, index) {
    if (index < 0 || index > this.size) {
        return;
    }

    if (index === 0) {
        this.prepend(value);
    } else {
        const node = new Node(value);
        let prev = this.head;

        for (let i = 0; i < index - 1; i++) {
            prev = prev.next;
        }

        node.next = prev.next;
        prev.next = node;
        this.size++;
    }
}
````

 - insert: Inserta un nodo en una posición específica. Si el índice es 0, se usa prepend. De lo contrario, recorre la lista hasta la posición anterior al índice, ajusta los punteros y actualiza el tamaño de la lista.

````javascript
removeFrom(index) {
    if (index < 0 || index >= this.size) {
        return null;
    }

    let removeNode;
    if (index === 0) {
        removeNode = this.head;
        this.head = this.head.next;
    } else {
        let prev = this.head;

        for (let i = 0; i < index - 1; i++) {
            prev = prev.next;
        }

        removeNode = prev.next;
        prev.next = removeNode.next;
    }

    this.size--;
    return removeNode.value;
}
````
- removeFrom: Elimina un nodo de una posición específica. Si el índice es 0, elimina la cabeza. De lo contrario, recorre la lista hasta la posición anterior al índice, ajusta los punteros y actualiza el tamaño de la lista.

````javascript
removeFirst() {
    if (this.isEmpty()) {
        return null;
    }

    const removeNode = this.head;
    this.head = this.head.next;
    this.size--;
    return removeNode.value;
}
````
-  removeFirst: Elimina el primer nodo (cabeza) y devuelve su valor. Ajusta la cabeza al siguiente nodo y reduce el tamaño de la lista.

````javascript
removeLast() {
    if (this.isEmpty()) {
        return null;
    }

    let current = this.head;
    let previous;

    if (this.size === 1) {
        this.head = null;
    } else {
        while (current.next) {
            previous = current;
            current = current.next;
        }

        previous.next = null;
    }

    this.size--;
    return current.value;
}
````
-  removeLast: Elimina el último nodo (cola) y devuelve su valor. Recorre la lista hasta el penúltimo nodo, ajusta el puntero del penúltimo nodo a null y reduce el tamaño de la lista.

````javascript
print() {
    if (this.isEmpty()) {
        console.log('Lista vacía');
    } else {
        let curr = this.head;
        let listValues = ``;

        while (curr) {
            listValues += `${curr.value} `;
            curr = curr.next;
        }

        console.log(listValues);
    }
}
````
-  print: Imprime los valores de la lista enlazada. Si la lista está vacía, imprime "Lista vacía". De lo contrario, recorre la lista y concatena los valores en una cadena que luego se imprime.

Uso de la Lista Enlazada.

