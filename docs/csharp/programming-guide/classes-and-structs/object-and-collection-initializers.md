---
title: Inicjatory obiektów i kolekcji — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 1f8ae023c414f8762139b194a9a8274218d0b5aa
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419372"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)

C#umożliwia utworzenie wystąpienia obiektu lub kolekcji i wykonywanie przypisań elementów członkowskich w pojedynczej instrukcji.

## <a name="object-initializers"></a>Inicjatory obiektów

Inicjatory obiektów umożliwiają przypisywanie wartości do dowolnych dostępnych pól lub właściwości obiektu w czasie jego tworzenia, bez konieczności wywoływania konstruktora, po którym występują wiersze instrukcji przypisania. Składnia inicjatora obiektów umożliwia określenie argumentów dla konstruktora lub pominięcie argumentów (i składni z nawiasami).  Poniższy przykład pokazuje, jak używać inicjatora obiektów z nazwanym typem, `Cat` i sposób wywoływania konstruktora bez parametrów. Zwróć uwagę na użycie właściwości, które są implementowane w klasie `Cat`. Aby uzyskać więcej informacji, zobacz [zaimplementowane właściwości](auto-implemented-properties.md).  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  
 
Składnia inicjatorów obiektów umożliwia utworzenie wystąpienia, a po nim przypisuje nowo utworzony obiekt z przypisanymi do niego właściwościami do zmiennej w przypisaniu.

Począwszy od C# 6, Inicjatory obiektów mogą ustawiać indeksatory oprócz przypisywania pól i właściwości. Rozważmy tę podstawową klasę `Matrix`:

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

Macierz tożsamości można zainicjować przy użyciu następującego kodu:

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

Dowolny dostępny indeksator zawierający dostępną metodę ustawiającą można użyć jako jednego z wyrażeń w inicjatorze obiektu, niezależnie od liczby lub typów argumentów. Argumenty indeksu tworzą lewą stronę przypisania, a wartość jest prawą stroną wyrażenia.  Na przykład są one prawidłowe, jeśli `IndexersExample` ma odpowiednie indeksatory:

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

Dla poprzedniego kodu do skompilowania typ `IndexersExample` musi mieć następujących członków:

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a>Inicjatory obiektów z typami anonimowymi

Chociaż inicjatorów obiektów można używać w dowolnym kontekście, są one szczególnie przydatne w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań. Wyrażenia zapytania często używają [anonimowych typów](./anonymous-types.md), które mogą być inicjowane tylko przy użyciu inicjatora obiektów, jak pokazano w poniższej deklaracji.  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

Typy anonimowe umożliwiają klauzulę `select` w wyrażeniu zapytania [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], aby przekształcić obiekty oryginalnej sekwencji do obiektów, których wartość i kształt mogą się różnić od oryginału. Jest to użyteczne, gdy chce się przechowywać tylko część informacji z każdego obiektu sekwencji. W poniższym przykładzie Załóżmy, że obiekt produktu (`p`) zawiera wiele pól i metod oraz że interesuje Cię tylko Tworzenie sekwencji obiektów zawierających nazwę produktu i cenę jednostkową.  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

Po wykonaniu tego zapytania zmienna `productInfos` będzie zawierać sekwencję obiektów, do których można uzyskać dostęp w instrukcji `foreach`, jak pokazano w tym przykładzie:  

```csharp
foreach(var p in productInfos){...}  
```

Każdy obiekt w nowym typie anonimowym ma dwie właściwości publiczne, które otrzymują takie same nazwy, jak właściwości lub pola w oryginalnym obiekcie. Możesz również zmienić nazwę pola podczas tworzenia typu anonimowego; Poniższy przykład zmienia nazwę pola `UnitPrice`, aby `Price`.  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a>Inicjatory kolekcji

Inicjatory kolekcji pozwalają określić jeden lub więcej inicjatorów elementów po zainicjowaniu typu kolekcji implementującego <xref:System.Collections.IEnumerable> i ma `Add` z odpowiednią sygnaturą jako metodę wystąpienia lub metodę rozszerzenia. Inicjatory elementów mogą być prostą wartością, wyrażeniem lub inicjatorem obiektu. Za pomocą inicjatora kolekcji nie trzeba określać wielu wywołań; Kompilator automatycznie dodaje wywołania.  
  
W poniższym przykładzie przedstawiono dwa proste Inicjatory kolekcji:  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

Poniższy inicjator kolekcji używa inicjatorów obiektów do inicjowania obiektów klasy `Cat` zdefiniowanej w poprzednim przykładzie. Należy zauważyć, że poszczególne inicjatory obiektów są umieszczone w nawiasach klamrowych i rozdzielone przecinkami.  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
Można określić [wartość null](../../language-reference/keywords/null.md) jako element w inicjatorze kolekcji, jeśli pozwala na to metoda `Add` kolekcji.  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 Można określić indeksowane elementy, jeśli kolekcja obsługuje indeksowanie odczytu/zapisu.
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

Poprzedni przykład generuje kod, który wywołuje <xref:System.Collections.Generic.Dictionary%602.Item(%600)>, aby ustawić wartości. Począwszy od C# 6, można inicjować słowniki i inne kontenery asocjacyjne przy użyciu następującej składni. Należy zauważyć, że zamiast składni indeksatora, z nawiasami i przypisaniem, używa obiektu z wieloma wartościami:

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

Ten inicjator przykładu wywołuje <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)>, aby dodać trzy elementy do słownika. Te dwa różne sposoby inicjowania kolekcji asocjacyjnych mają nieco inne zachowanie ze względu na to, że metoda wywołuje kompilator. Obie warianty pracują z klasą `Dictionary`. Inne typy mogą obsługiwać tylko jedną lub drugą w oparciu o ich publiczny interfejs API.

## <a name="examples"></a>Przykłady

Poniższy przykład łączy koncepcje inicjatorów obiektów i kolekcji.

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

Poniższy przykład pokazuje obiekt, który implementuje <xref:System.Collections.IEnumerable> i zawiera metodę `Add` z wieloma parametrami, używa inicjatora kolekcji z wieloma elementami na liście, które odpowiadają sygnaturze metody `Add`.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

Metody `Add` mogą użyć słowa kluczowego `params`, aby przyjąć zmienną liczbę argumentów, jak pokazano w poniższym przykładzie. Ten przykład ilustruje również niestandardową implementację indeksatora w celu zainicjowania kolekcji przy użyciu indeksów.

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [LINQ w C#](../../linq/index.md)
- [Typy anonimowe](anonymous-types.md)
