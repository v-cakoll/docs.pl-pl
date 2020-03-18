---
title: Inicjatory obiektów i kolekcji — przewodnik programowania języka C#
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: ae8741e2f29db0a470ad8d3b121375fbdeaff0d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170198"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)

C# umożliwia tworzenie wystąpienia obiektu lub kolekcji i wykonywania przypisań elementów członkowskich w jednej instrukcji.

## <a name="object-initializers"></a>Inicjatory obiektów

Inicjatory obiektów umożliwiają przypisywanie wartości do dowolnych dostępnych pól lub właściwości obiektu w czasie jego tworzenia, bez konieczności wywoływania konstruktora, po którym występują wiersze instrukcji przypisania. Składnia inicjatora obiektów umożliwia określenie argumentów dla konstruktora lub pominięcie argumentów (i składni z nawiasami).  W poniższym przykładzie pokazano, jak używać inicjatora obiektów o nazwanym typie `Cat` i jak wywołać konstruktora bezparametrowego. Należy zwrócić uwagę na użycie właściwości `Cat` implementowane automatycznie w klasie. Aby uzyskać więcej informacji, zobacz [Właściwości implementowane automatycznie](auto-implemented-properties.md).  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  

Składnia inicjaalizatorów obiektów umożliwia utworzenie wystąpienia, a następnie przypisuje nowo utworzony obiekt, z jego przypisanymi właściwościami, do zmiennej w przydziale.

Począwszy od C# 6 inicjatory obiektów można ustawić indeksatory, oprócz przypisywania pól i właściwości. Rozważmy `Matrix` tę podstawową klasę:

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

Macierz tożsamości można zainicjować następującym kodem:

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

Każdy indeksator dostępny, który zawiera zestawseter dostępne może służyć jako jedno z wyrażeń w inicjatora obiektu, niezależnie od liczby lub typów argumentów. Argumenty indeksu tworzą lewą stronę przypisania, a wartość jest po prawej stronie wyrażenia.  Na przykład wszystkie te `IndexersExample` są prawidłowe, jeśli ma odpowiednie indeksatory:

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Size = Math.PI,
    ['C',4] = "Middle C"
}
```

Dla poprzedniego kodu do `IndexersExample` skompilowania, typ musi mieć następujące elementy członkowskie:

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a>Inicjatory obiektów z typami anonimowymi

Chociaż inicjatory obiektów mogą być używane w dowolnym kontekście, są one szczególnie przydatne w wyrażeniach kwerend LINQ. Wyrażenia kwerendy często używają [typów anonimowych](./anonymous-types.md), które mogą być inicjowane tylko przy użyciu inicjatora obiektów, jak pokazano w poniższej deklaracji.  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

Typy anonimowe `select` włączyć klauzulę w wyrażeniu kwerendy LINQ do przekształcania obiektów oryginalnej sekwencji do obiektów, których wartość i kształt może różnić się od oryginału. Jest to użyteczne, gdy chce się przechowywać tylko część informacji z każdego obiektu sekwencji. W poniższym przykładzie załóżmy,`p`że obiekt produktu ( ) zawiera wiele pól i metod i że jesteś zainteresowany tylko utworzeniesekwencji obiektów, które zawierają nazwę produktu i cenę jednostkową.  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

Po wykonaniu tej kwerendy zmienna `productInfos` będzie zawierać sekwencję obiektów, `foreach` do których można uzyskać dostęp w instrukcji, jak pokazano w tym przykładzie:  

```csharp
foreach(var p in productInfos){...}  
```

Każdy obiekt w nowym typie anonimowym ma dwie właściwości publiczne, które otrzymują takie same nazwy jak właściwości lub pola w oryginalnym obiekcie. Można również zmienić nazwę pola podczas tworzenia typu anonimowego; w poniższym przykładzie `UnitPrice` zmienia `Price`nazwę pola na .  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a>Inicjatory kolekcji

Inicjatory kolekcji pozwalają określić jeden lub więcej inicjatorów elementu <xref:System.Collections.IEnumerable> podczas `Add` inicjowania typu kolekcji, który implementuje i ma odpowiedni podpis jako metodę wystąpienia lub metodę rozszerzenia. Inicjatory elementu może być wartość prostą, wyrażenie lub inicjator obiektu. Za pomocą inicjatora kolekcji, nie trzeba określić wiele wywołań; kompilator automatycznie dodaje wywołania.  
  
W poniższym przykładzie przedstawiono dwa proste inicjatory kolekcji:  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

Poniższy inicjator kolekcji używa inicjatorów `Cat` obiektów do inicjowania obiektów klasy zdefiniowanej w poprzednim przykładzie. Należy zauważyć, że poszczególne inicjatory obiektów są umieszczone w nawiasach klamrowych i rozdzielone przecinkami.  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
Można określić [null](../../language-reference/keywords/null.md) jako element w inicjatora `Add` kolekcji, jeśli metoda kolekcji zezwala na to.  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 Można określić elementy indeksowane, jeśli kolekcja obsługuje indeksowanie odczytu /zapisu.
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

Poprzedni przykład generuje kod, który <xref:System.Collections.Generic.Dictionary%602.Item(%600)> wywołuje, aby ustawić wartości. Przed C# 6, można zainicjować słowniki i inne kontenery zestosujące przy użyciu następującej składni. Należy zauważyć, że zamiast składni indeksatora, z nawiasami i przypisaniem, używa obiektu z wieloma wartościami:

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

Ten przykład inicjatora wywołuje, <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> aby dodać trzy elementy do słownika. Te dwa różne sposoby inicjowania kolekcje zeszalenie mają nieco inne zachowanie ze względu na metodę wywołuje generuje kompilator. Oba warianty działają `Dictionary` z klasą. Inne typy mogą obsługiwać tylko jeden lub drugi na podstawie ich publicznego interfejsu API.

## <a name="examples"></a>Przykłady

Poniższy przykład łączy pojęcia inicjali obiektów i kolekcji.

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

W poniższym przykładzie przedstawiono <xref:System.Collections.IEnumerable> obiekt, `Add` który implementuje i zawiera metodę z wieloma parametrami, Używa inicjatora `Add` kolekcji z wieloma elementami na element na listę, które odpowiadają podpismetody.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

`Add`metody można użyć `params` słowa kluczowego do podjęcia zmiennej liczby argumentów, jak pokazano w poniższym przykładzie. W tym przykładzie przedstawiono również implementację niestandardową indeksatora, aby zainicjować kolekcję przy użyciu indeksów.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [LINQ w C#](../../linq/index.md)
- [Typy anonimowe](anonymous-types.md)
