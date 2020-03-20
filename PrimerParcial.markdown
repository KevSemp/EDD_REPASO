## TDA
Tipos de datos creados por el programador, que deben ser opacos (accesibilidad)

+ Create a list by starting a line with `+`, `-`, or `*`

+ Tipos de datos 
  + Enteros,reales,booleanos,caracteres
Enumerados,arreglos
Son Opacos


## Listas

+ Lista Simple 
es aquella que el apuntador unicamente va hacia siguiente 

+ Creamos nuestra clase nodo

```c++
class Nodo{
public:
    NodoS(string palabra_,string remplazar_){
        siguiente=0;  //Solo tendra un apuntador a siguiente
        palabra = palabra_;
        remplazar=remplazar_;
    }
    
    Nodo *getSiguiente(){return siguiente;}
    
    void setSiguiente(NodoS *n){siguiente=n;}
    
    string getPalabra(){return palabra;}
    
    string getRemplazar(){return remplazar;}

    void setPalabra(string palabra_){
        palabra = palabra_;
    }
    void setRemplazar(string remplazar_){
        palabra = remplazar_;
    }


private:
    Nodo* siguiente;
    //En este ejemplo tendremos que el nodo tendra dos atributos de tipo string
    string palabra;  
    string remplazar;
};

```


+ Creamamos nuestra clase Lista simple

```c++
class ListaSimple{
public:
    ListaSimple(){
    //Tendra atributos que haran referencia al primer y ultio nodo
        primero=0;
        ultimo=0;
     //Este size nos permitira saber la longitud de nuestra lista 
        size=0;
    }
        int getTamanio(){return size;}
    }

```


+ Metodo insertar en una lista simple
```c++
class    void insertar(string palabra,string remplazo){
        NodoS *n = new NodoS(palabra,remplazo); //Reservamos el nuevo nodo en memoria
        //Primero verificamos si la lista esta vacia
        if(this->estaVacia()){
            this->primero=n; //primero sera el nuevo nodo
            this->ultimo =n; // utlimo sera el nuevo nodo
            //esto porque es el primer nodo de la lista
            this->size++;
        }else{
          //Decimos que si no, el apuntador siguiente del ulitmo nodo ahora apuntara al nuevo nodo 
            this->ultimo->setSiguiente(n); 
            this->ultimo=n;  // ultimo sera ahora el nuevo nodo, esto porque agregamos al final de la lista
            this->size++;
        }
    }

```



+ Metodo borrar por poscion en una lista doble
```c++
void borrarPos(int pos){
        if(this->primero!=0){//se realiza la validación que la cabeza no esté vacía
            if(pos >= 0 && pos<= this->size){ // se valida que se desee eliminar un elemento existente
                if(pos==0 && this->size ==1){ //validacion para que si se desea eliminar el primero y el tamaño es
                    primero = 0;                  // el nodo incial se declara vacio
                    ultimo = 0;                   // el nodo final se declara vacio
                    size = 0;                   // el tamaño de la lista es
                }
                else if(pos==0){              // si desea eliminar el primero
                    Nodo *aux = this->primero->getSiguiente();   // instanciamos un nodo auxiliar que obtenga el siguiente del primero
                    primero->setSiguiente(0);                    // quitamos el puntero a siguiente de la cabeza
                    primero = aux;                          //el primero elemento de la lista será el auxiliar
                    primero->setAnterior(0);                  // el anterior del primero será null
                    this->size--;                         //decremento al tamaño de la lista

                }
                else if(pos == this->size-1){          //si desea eliminar el ultimo elemento de la lista
                    Nodo *aux = this->ultimo->getAnterior(); // instanciamos un nodo auxiliar que obtenga el anterior del ultimo
                    ultimo = aux;                          // ahora decimos que el ultimo de la lista será aux
                    ultimo->setSiguiente(0);                     //ahora el puntero del ultimo nodo apunta a null
                    this->size--;                       // decremento al tamaño de la lista
                }
                else if(pos>0 && pos < this->size-1){ //si el elemento que desea eliminar no es el ultimo ni el primero
                    Nodo *aux = this->primero;              //creamos un nodo auxiliar que tenga la cabeza de la lista
                    int x = 0;                            // declaramos variable para obtener posicion deseada
                    while(aux!=0){                        //recorremos la lista, mientras no sea vacia


                        if(x==pos){                     //validacion  para encontrar la posicion
                            break;                        //salimos de while
                        }// incremento para encontrar posicion
                        aux = aux->getSiguiente();              // obtenemos el nodo el cual se desea eliminar
                        x++;
                    }
                    aux->getAnterior()->setSiguiente(aux->getSiguiente());   // decimos que el anterior del <a eliminar> tendrá de siguiente el <eliminar>.siguiente
                    aux->getSiguiente()->setAnterior(aux->getAnterior()); // ahora decimos que el siguiente del <a eliminar> tendra de anterior el <eliminar>.anterior
                    aux->setSiguiente(0);                             //de desapunta el puntero siguiente a null
                    aux->setAnterior(0);                            // se desapunta el puntero anterior a null
                    size--;                                       // ya que no utilizo destructor, no se elimina completamente de la memorio pero
                }                                                  // se desvincula de la lista, y esta ya no se queda guardada en ella
            }                                                     // en otras palaabras queda en el aire
        }
    }

```




