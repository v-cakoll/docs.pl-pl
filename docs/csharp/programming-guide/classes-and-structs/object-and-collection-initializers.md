---
title: Inicjatory obiektów i kolekcji - C# przewodnik programowania
ms.custom: seodec18
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 6c713072e120f2b5a6740add296c957d499c93c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646221"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)

C#Pozwala utworzyć wystąpienie obiektu lub kolekcji i wykonywać przypisań składowych w pojedynczej instrukcji.

## <a name="object-initializers"></a>Inicjatory obiektów

Inicjatory obiektów umożliwiają przypisywanie wartości do dowolnych dostępnych pól lub właściwości obiektu w czasie jego tworzenia, bez konieczności wywoływania konstruktora, po którym występują wiersze instrukcji przypisania. Składnia inicjatora obiektów umożliwia określenie argumentów dla konstruktora lub pominięcie argumentów (i składni z nawiasami).  Poniższy przykład pokazuje, jak używać inicjatora obiektów z typem nazwanym `Cat` i jak wywołać konstruktora bez parametrów. Zwróć uwagę na użycie właściwości zaimplementowane automatycznie w `Cat` klasy. Aby uzyskać więcej informacji, zobacz [implemented Properties](auto-implemented-properties.md).  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  
 
Składnię inicjatorów obiektów można utworzyć wystąpienia, a po tym przypisuje nowo utworzony obiekt, za pomocą właściwości przypisane do zmiennej w ramach przypisania.

Począwszy od C# 6, obiektu, inicjatory można ustawić indeksatorów, oprócz przypisywanie pola i właściwości. Należy wziąć pod uwagę to podstawowe `Matrix` klasy:

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

Można zainicjować macierzą następującym kodem:

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

Dostęp indeksatora, który zawiera dostępnej metody ustawiającej może służyć jako jedno z wyrażeń w inicjatorze obiektu, niezależnie od liczby i typy argumentów. Argumenty indeksu formularza po lewej stronie przypisania, a wartość jest po prawej stronie wyrażenia.  Na przykład są to wszystkie prawidłowe, gdy `IndexersExample` ma odpowiednie indeksatory:

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Baz = Math.PI,
    ['C',4] = "Middle C"
}
```

Dla poprzedniego kodu skompilować `IndexersExample` typ musi zawierać następujące elementy:

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
}
```

## <a name="object-initializers-with-anonymous-types"></a>Inicjatory obiektów z typami anonimowymi

Mimo że inicjatorów obiektów można używać w dowolnym kontekście, są one szczególnie użyteczne w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań. Wyrażeniach zapytań często są używane [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), który może być inicjowane tylko przy użyciu inicjatora obiektów, jak pokazano w poniższej deklaracji.  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

Typy anonimowe umożliwiają `select` w klauzuli [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniu do przekształcenia obiektów oryginalnej sekwencji w obiekty, których wartość i kształt mogą różnić się od oryginalnego zapytania. Jest to użyteczne, gdy chce się przechowywać tylko część informacji z każdego obiektu sekwencji. W poniższym przykładzie przyjęto założenie, że obiekt produktu (`p`) zawiera wiele pól i metod, i że możesz jest zainteresowany wyłącznie utworzeniem sekwencji obiektów, które zawierają nazwę produktu i cenę jednostkową.  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

Gdy to zapytanie jest wykonywane, `productInfos` zmienna będzie zawierać sekwencję obiektów, które mogą być udostępniane w `foreach` instrukcji, jak pokazano w poniższym przykładzie:  

```csharp
foreach(var p in productInfos){...}  
```

Każdy obiekt w nowym typie anonimowym ma dwie właściwości publiczne, które odbierają takie same nazwy właściwości lub pola w oryginalnym obiekcie. Możesz również zmienić nazwę pola, podczas tworzenia typu anonimowego; w poniższym przykładzie nazwa `UnitPrice` pole `Price`.  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a>Inicjatory kolekcji

Inicjatory kolekcji pozwalają określić jedną lub więcej inicjatory elementów podczas inicjowania kolekcji typu, który implementuje <xref:System.Collections.IEnumerable> i ma `Add` z odpowiednim podpisem jako metodę wystąpienia lub metodę rozszerzenia. Inicjatory elementów mogą być wartościami prostymi, wyrażenie lub inicjatora obiektu. Za pomocą inicjatora kolekcji, nie trzeba określać wielu wywołań; Kompilator sam doda te wywołania automatycznie.  
  
W poniższym przykładzie pokazano dwa proste inicjatory kolekcji:  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

Następujący inicjator kolekcji używa inicjatorów obiektów w celu zainicjowania obiektów klasy `Cat` klasy zdefiniowanej w poprzednim przykładzie. Należy zauważyć, że poszczególne inicjatory obiektów są umieszczone w nawiasach klamrowych i rozdzielone przecinkami.  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
Można określić [null](../../language-reference/keywords/null.md) jako element w inicjatorze kolekcji Jeśli kolekcji `Add` zezwala na to metoda.  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 Można określić elementy indeksowane, jeżeli obsługuje kolekcji odczytu i zapisu indeksowania.
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

Poprzedni przykład generuje kod, który wywołuje <xref:System.Collections.Generic.Dictionary%602.Item(%600)> można ustawić wartości. Począwszy od C# 6, można inicjować słowników i inne kontenery asocjacyjne przy użyciu następującej składni. Zwróć uwagę, że zamiast składni indeksatora, za pomocą nawiasów i przypisania, używa obiekt z wieloma wartościami:

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

Ten przykład inicjatora wywołuje <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> można dodać trzy elementy do słownika. Te dwa różne sposoby inicjowania kolekcji asocjacyjnych ma nieco inaczej, ze względu na wywołania metody, które kompilator generuje. Oba warianty pracować `Dictionary` klasy. Inne typy mogą obsługują tylko jeden lub innych zależności na ich publicznego interfejsu API.

## <a name="examples"></a>Przykłady

Poniższy przykład łączy koncepcji inicjatory obiektów i kolekcji.

[!code-csharp-interactive[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

W poniższym przykładzie pokazano obiekt, który implementuje <xref:System.Collections.IEnumerable> i zawiera `Add` metody z wieloma parametrami, używa inicjatora kolekcji z wieloma elementami każdego elementu na liście, które odpowiadają podpis `Add`metody.

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

`Add` można użyć metody `params` — słowo kluczowe, aby móc zmienną liczbę argumentów, jak pokazano w poniższym przykładzie. W przykładzie pokazano również niestandardową implementację indeksatora zainicjować kolekcji za pomocą indeksów.

[!code-csharp-interactive[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Wyrażenia zapytań LINQ](../linq-query-expressions/index.md)
- [Typy anonimowe](anonymous-types.md)
