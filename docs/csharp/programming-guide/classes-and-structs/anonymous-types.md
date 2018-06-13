---
title: Typy anonimowe (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
ms.openlocfilehash: 40c709e8a68f3a095672a9d4b7aacde5c62e12af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33314219"
---
# <a name="anonymous-types-c-programming-guide"></a>Typy anonimowe (Przewodnik programowania w języku C#)
Typy anonimowe zapewnić wygodny sposób Hermetyzowanie zbiór właściwości tylko do odczytu do pojedynczego obiektu bez konieczności jawnie najpierw zdefiniować typu. Nazwa typu jest generowanych przez kompilator i nie jest dostępna na poziomie kodu źródłowego. Typ każdej właściwości jest wykryta przez kompilator.  
  
 Typy anonimowe są tworzone przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) operator wraz z inicjatora obiektu. Aby uzyskać więcej informacji na temat inicjatory obiektów, zobacz [inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
 W poniższym przykładzie przedstawiono typu anonimowego, który został zainicjowany przy dwie właściwości o nazwie `Amount` i `Message`.  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Typy anonimowe są zazwyczaj używane w [wybierz](../../../csharp/language-reference/keywords/select-clause.md) klauzuli wyrażenia zapytania do zwrócenia podzbiór właściwości z każdego obiektu w sekwencji źródłowej. Aby uzyskać więcej informacji o zapytaniach znajduje się w temacie [wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
 Typy anonimowe zawiera co najmniej jeden publiczny właściwości tylko do odczytu. Nie inne rodzaje elementów członkowskich klasy, takie jak metody lub zdarzenia, są prawidłowe. Wyrażenie, które służy do inicjowania właściwości nie może być `null`, funkcję anonimową lub typu wskaźnika.  
  
 Najbardziej typowym scenariuszem jest zainicjować anonimowy typ o właściwościach z innego typu. W poniższym przykładzie założono, że istnieje klasa, która nosi nazwę `Product`. Klasa `Product` obejmuje `Color` i `Price` właściwości, oraz inne właściwości, które nie są zainteresowane. Zmienna `products` jest kolekcją `Product` obiektów. Rozpoczyna się od deklaracji typu anonimowego `new` — słowo kluczowe. Deklaracja inicjuje nowy typ, który używa tylko dwie właściwości z `Product`. Powoduje to mniejszą ilość danych, które ma zostać zwrócona w zapytaniu.  
  
 Jeśli nie określisz nazwy elementów członkowskich w typu anonimowego, kompilator zapewnia elementy członkowskie typu anonimowego taką samą nazwę jak właściwość używana do ich inicjowania. Podaj nazwę właściwości, która jest inicjowany z wyrażeniem, jak pokazano w poprzednim przykładzie. W poniższym przykładzie nazwy właściwości typu anonimowego są `Color` i `Price`.  
  
 [!code-csharp[csRef30Features#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/anonymous-types_1.cs)]  
  
 Zazwyczaj użycie typu anonimowego można zainicjować zmiennej, należy zadeklarować zmienną jako niejawnie wpisane zmiennej lokalnej za pomocą [var](../../../csharp/language-reference/keywords/var.md). Nazwa typu nie można określić w deklaracji zmiennej, ponieważ tylko kompilatora ma dostęp do podstawowej nazwy typu anonimowego. Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Można utworzyć tablicę elementów anonimowo typu łącząc niejawnie wpisane zmiennej lokalnej i niejawnie wpisane tablicy, jak pokazano w poniższym przykładzie.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Uwagi  
 Typy anonimowe są [klasy](../../../csharp/language-reference/keywords/class.md) typy, które pochodzi bezpośrednio z [obiektu](../../../csharp/language-reference/keywords/object.md), i nie można rzutować do dowolnego typu, z wyjątkiem [obiektu](../../../csharp/language-reference/keywords/object.md). Kompilator zawiera nazwę dla każdego typu anonimowego, mimo że aplikacji nie można do niego dostęp. Z punktu widzenia środowiska CLR typu anonimowego nie różni się od innego typu odwołania.  
  
 Jeśli co najmniej dwa inicjatory anonimowego obiektu w zestawie określić sekwencję właściwości, które znajdują się w tej samej kolejności i mają takie same nazwy i typy, kompilator traktuje obiekty jako wystąpień tego samego typu. Mają te same informacje generowane przez kompilator typu.  
  
 Nie można zadeklarować pola, właściwości, zdarzenia lub typ zwracany metody jako mający typu anonimowego. Podobnie nie można zadeklarować formalny parametr metody, właściwości, konstruktora lub indeksatora jako mający typu anonimowego. Aby przekazać typu anonimowego lub kolekcję, która zawiera typy anonimowe jako argument do metody, można zadeklarować jako obiekt typu parametru. Jednak w ten sposób pozbawia sensu silne wpisywanie. Jeśli należy przechowywać wyniki zapytania lub przekaż je poza granicami — metoda, rozważ użycie zwykłej nazwanego struktury lub klasy zamiast typu anonimowego.  
  
 Ponieważ <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> metody na typach anonimowego są definiowane w postaci liczby `Equals` i `GetHashCode` metody właściwości dwa wystąpienia tego samego typu anonimowego są takie same, tylko wtedy, gdy ich właściwości są takie same.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [Wprowadzenie do korzystania z LINQ w C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
