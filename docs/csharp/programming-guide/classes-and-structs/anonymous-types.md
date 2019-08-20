---
title: Typy anonimowe C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#]
- C# Language, anonymous types
ms.assetid: 59c9d7a4-3b0e-475e-b620-0ab86c088e9b
ms.openlocfilehash: 93f02b8a0f828be89c6a1b7bfcdc6ba2a2a93e81
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597194"
---
# <a name="anonymous-types-c-programming-guide"></a>Typy anonimowe (Przewodnik programowania w języku C#)

Typy anonimowe zapewniają wygodny sposób hermetyzowania zestawu właściwości tylko do odczytu w jednym obiekcie bez konieczności jawnego definiowania typu. Nazwa typu jest generowana przez kompilator i nie jest dostępna na poziomie kodu źródłowego. Typ każdej właściwości jest wnioskowany przez kompilator.  
  
 Typy anonimowe można tworzyć za pomocą operatora [New](../../language-reference/operators/new-operator.md) wraz z inicjatorem obiektu. Aby uzyskać więcej informacji na temat inicjatorów obiektów, zobacz [Inicjatory obiektów i kolekcji](./object-and-collection-initializers.md).  
  
 Poniższy przykład przedstawia typ anonimowy, który jest inicjowany z dwiema właściwościami `Amount` o `Message`nazwie i.  
  
```csharp  
var v = new { Amount = 108, Message = "Hello" };  
  
// Rest the mouse pointer over v.Amount and v.Message in the following  
// statement to verify that their inferred types are int and string.  
Console.WriteLine(v.Amount + v.Message);  
```  
  
 Typy anonimowe są zwykle używane w klauzuli [SELECT](../../language-reference/keywords/select-clause.md) wyrażenia zapytania w celu zwrócenia podzestawu właściwości z każdego obiektu w sekwencji źródłowej. Aby uzyskać więcej informacji o zapytaniach, zobacz [wyrażenia zapytań LINQ](../linq-query-expressions/index.md).  
  
 Typy anonimowe zawierają co najmniej jedną publiczną właściwość tylko do odczytu. Żadne inne rodzaje elementów członkowskich klasy, takie jak metody lub zdarzenia, są prawidłowe. Wyrażenie, które jest używane do inicjowania właściwości, nie może `null`być funkcją anonimową ani typem wskaźnika.  
  
 Najbardziej typowym scenariuszem jest zainicjowanie typu anonimowego z właściwościami innego typu. W poniższym przykładzie Załóżmy, że Klasa istnieje o nazwie `Product`. Klasy `Product` `Price` obejmują `Color` i właściwości, a także inne właściwości, które nie są zainteresowane. Zmienna `products` jest`Product` kolekcją obiektów. Deklaracja typu anonimowego zaczyna `new` się od słowa kluczowego. Deklaracja inicjuje nowy typ, który używa tylko dwóch właściwości z `Product`. Powoduje to zwrócenie mniejszej ilości danych w zapytaniu.  
  
 Jeśli nie określisz nazw składowych w typie anonimowym, kompilator poda elementy członkowskie typu anonimowego o tej samej nazwie, co właściwość używana do ich zainicjowania. Należy podać nazwę właściwości, która jest inicjowana za pomocą wyrażenia, jak pokazano w poprzednim przykładzie. W poniższym przykładzie nazwy właściwości typu anonimowego to `Color` i. `Price`  
  
 [!code-csharp[csRef30Features#81](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csRef30Features/CS/csref30.cs#81)]  
  
 Typowo, jeśli używasz typu anonimowego do inicjowania zmiennej, deklarujesz zmienną jako niejawnie wpisaną zmienną lokalną przy użyciu [var](../../language-reference/keywords/var.md). Nie można określić nazwy typu w deklaracji zmiennej, ponieważ tylko kompilator ma dostęp do podstawowej nazwy typu anonimowego. Aby uzyskać więcej informacji `var`na temat, zobacz niejawnie [wpisane zmienne lokalne](./implicitly-typed-local-variables.md).  
  
 Można utworzyć tablicę elementów o jednoznacznie określonym typie, łącząc niejawnie wpisaną zmienną lokalną i niejawnie wpisaną tablicę, jak pokazano w poniższym przykładzie.  
  
```csharp  
var anonArray = new[] { new { name = "apple", diam = 4 }, new { name = "grape", diam = 1 }};  
```  
  
## <a name="remarks"></a>Uwagi  
 Typy anonimowe to typy [klas](../../language-reference/keywords/class.md) , które są wyprowadzane bezpośrednio z [obiektu](../../language-reference/keywords/object.md)i nie mogą być rzutowane do żadnego typu poza [obiektem](../../language-reference/keywords/object.md). Kompilator zawiera nazwę dla każdego typu anonimowego, chociaż aplikacja nie może uzyskać do niej dostępu. Z perspektywy środowiska uruchomieniowego języka wspólnego typ anonimowy nie różni się od żadnego innego typu odwołania.  
  
 Jeśli co najmniej dwa anonimowe Inicjatory obiektów w zestawie określają sekwencję właściwości, które są w tej samej kolejności i mają takie same nazwy i typy, kompilator traktuje obiekty jako wystąpienia tego samego typu. Korzystają one z tych samych informacji o typie wygenerowanym przez kompilator.  
  
 Nie można zadeklarować pola, właściwości, zdarzenia lub typu zwracanego metody jako typu anonimowego. Podobnie nie można zadeklarować formalnego parametru metody, właściwości, konstruktora lub indeksatora jako typu anonimowego. Aby przekazać typ anonimowy lub kolekcję, która zawiera typy anonimowe jako argument metody, można zadeklarować parametr jako obiekt typu. Jednak dzięki temu przeznaczeniem jest silne wpisywanie. Jeśli musisz przechowywać wyniki zapytania lub przekazać je poza granicą metody, rozważ użycie zwykłej nazwanej struktury lub klasy zamiast typu anonimowego.  
  
 Ponieważ metody <xref:System.Object.GetHashCode%2A> `Equals` i dla typów anonimowych są zdefiniowane w kategoriach i `GetHashCode` metodach właściwości, dwa wystąpienia tego samego typu anonimowego są równe tylko wtedy, gdy wszystkie ich właściwości są równe. <xref:System.Object.Equals%2A>  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Inicjatory obiektów i kolekcji](./object-and-collection-initializers.md)
- [Wprowadzenie do korzystania z LINQ w C#](../concepts/linq/getting-started-with-linq.md)
- [Wyrażenia zapytania LINQ](../linq-query-expressions/index.md)
