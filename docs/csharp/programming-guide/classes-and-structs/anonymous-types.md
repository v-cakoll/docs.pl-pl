---
title: Anonimowe typy - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
ms.openlocfilehash: 7d8bdc5ceef5d82e4bc7e13ee932985cae6c2c10
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398545"
---
# <a name="anonymous-types-c-programming-guide"></a>Typy anonimowe (Przewodnik programowania w języku C#)

Typy anonimowe umożliwiają wygodne do hermetyzacji zbiór właściwości tylko do odczytu w jeden obiekt bez konieczności jawne zdefiniowanie typu najpierw. Nazwa typu jest generowanych przez kompilator i nie jest dostępna na poziomie kodu źródłowego. Typ każdej właściwości jest wnioskowany przez kompilator.  
  
 Typy anonimowe są tworzone przy użyciu [nowe](../../../csharp/language-reference/operators/new-operator.md) operator wraz z inicjatora obiektu. Aby uzyskać więcej informacji na temat inicjatorów obiektów zobacz [inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
 Poniższy przykład przedstawia typ anonimowy, który jest inicjowany za pomocą dwie właściwości o nazwie `Amount` i `Message`.  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Typy anonimowe są zazwyczaj używane w [wybierz](../../../csharp/language-reference/keywords/select-clause.md) klauzula w wyrażeniu zapytania do zwrócenia podzbiór właściwości z każdego obiektu w sekwencji źródłowej. Aby uzyskać więcej informacji o zapytaniach, zobacz [wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
 Typy anonimowe zawierają co najmniej jeden publiczny właściwości tylko do odczytu. Nie innych rodzajów elementów członkowskich klasy takich jak metody lub zdarzenia, są prawidłowe. Wyrażenie, które służy do inicjowania właściwości nie może być `null`, funkcja anonimowa lub typ wskaźnika.  
  
 Najbardziej typowym scenariuszem jest do zainicjowania typu anonimowego z właściwościami z innego typu. W poniższym przykładzie przyjęto założenie, że istnieje klasa, która nosi nazwę `Product`. Klasa `Product` obejmuje `Color` i `Price` właściwości wraz z innych właściwości, które nie są zainteresowani. Zmienna `products` to zbiór `Product` obiektów. Deklaracja typu anonimowego zaczyna się od `new` — słowo kluczowe. Deklaracja inicjuje nowy typ, który używa tylko dwie właściwości z `Product`. Powoduje to mniejszą ilość danych, które mają zostać zwrócone w zapytaniu.  
  
 Jeśli nie określisz nazwy elementów członkowskich w typu anonimowego, kompilator zapewnia składowe typu anonimowego taką samą nazwę jak właściwość używana do ich inicjowania. Należy podać nazwę właściwości, który jest inicjowany za pomocą wyrażenia, jak pokazano w poprzednim przykładzie. W poniższym przykładzie są nazwami właściwości typu anonimowego `Color` i `Price`.  
  
 [!code-csharp[csRef30Features#81](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csRef30Features/CS/csref30.cs#81)]  
  
 Zazwyczaj, gdy używasz typu anonimowego można zainicjować zmiennej został zadeklarowany zmiennej jako niejawnie typizowanej zmiennej lokalnej za pomocą [var](../../../csharp/language-reference/keywords/var.md). Nie można określić nazwę typu w deklaracji zmiennej, ponieważ tylko kompilator ma dostęp do podstawowej nazwy typu anonimowego. Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Łącząc niejawnie typizowanej zmiennej lokalnej i niejawnie typizowana tablica, można utworzyć tablicy anonimowo typizowanych elementów, jak pokazano w poniższym przykładzie.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Uwagi  
 Typy anonimowe są [klasy](../../../csharp/language-reference/keywords/class.md) typy, które pochodzą bezpośrednio z [obiektu](../../../csharp/language-reference/keywords/object.md), i nie można rzutować do dowolnego typu z wyjątkiem [obiektu](../../../csharp/language-reference/keywords/object.md). Kompilator zapewnia nazwę dla każdego typu anonimowego, mimo że aplikacja nie można do niego dostęp. Z punktu widzenia środowiska uruchomieniowego języka wspólnego typu anonimowego nie różni się od innego typu odwołania.  
  
 Jeśli co najmniej dwóch inicjatory obiekt anonimowy w zestawie, należy określić sekwencję właściwości, które znajdują się w tej samej kolejności i mają takie same nazwy i typy, kompilator traktuje obiektów jako wystąpienia tego samego typu. Współużytkują one te same informacje o typie wygenerowanym przez kompilator.  
  
 Nie można zadeklarować pola, właściwości, zdarzenia lub zwracany typ metody jako mające typ anonimowy. Podobnie nie można zadeklarować formalny parametr metody, właściwości, Konstruktor lub indeksator jako mające typ anonimowy. Aby przekazać typu anonimowego lub kolekcję, która zawiera typy anonimowe jako argument do metody, można zadeklarować parametru jako obiekt typu. Jednak w ten sposób pozbawia silne wpisywanie. Jeśli należy przechowywać wyniki zapytania lub przekazywać je poza granice metody, należy wziąć pod uwagę przy użyciu zwykłej nazwanej struktury lub klasy zamiast typu anonimowego.  
  
 Ponieważ <xref:System.Object.Equals%2A> i <xref:System.Object.GetHashCode%2A> metod anonimowych typów są definiowane w kategoriach `Equals` i `GetHashCode` metody, właściwości dwóch wystąpień tego samego typu anonimowego są takie same, tylko wtedy, gdy ich właściwości są takie same.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
- [Wprowadzenie do korzystania z LINQ w C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
