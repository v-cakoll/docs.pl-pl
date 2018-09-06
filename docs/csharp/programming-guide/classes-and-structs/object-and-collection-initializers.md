---
title: Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: def33041c4202c80aad9f08d1ff8d9dbbc477061
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892428"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)
Inicjatory obiektów umożliwiają przypisywanie wartości do dowolnych dostępnych pól lub właściwości obiektu w czasie jego tworzenia, bez konieczności wywoływania konstruktora, po którym występują wiersze instrukcji przypisania. Składnia inicjatora obiektów umożliwia określenie argumentów dla konstruktora lub pominięcie argumentów (i składni z nawiasami).  Poniższy przykład pokazuje, jak używać inicjatora obiektów z typem nazwanym `Cat` i jak wywołać konstruktora domyślnego. Zwróć uwagę na użycie właściwości zaimplementowane automatycznie w `Cat` klasy. Aby uzyskać więcej informacji, zobacz [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
Składnię inicjatorów obiektów można utworzyć wystąpienia, a po tym przypisuje nowo utworzony obiekt, za pomocą właściwości przypisane do zmiennej w ramach przypisania.
  
## <a name="object-initializers-with-anonymous-types"></a>Inicjatory obiektów z typami anonimowymi  
 Mimo że inicjatorów obiektów można używać w dowolnym kontekście, są one szczególnie użyteczne w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań. Wyrażeniach zapytań często są używane [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), który może być inicjowane tylko przy użyciu inicjatora obiektów, jak pokazano w poniższej deklaracji.  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 Typy anonimowe umożliwiają `select` w klauzuli [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniu do przekształcenia obiektów oryginalnej sekwencji w obiekty, których wartość i kształt mogą różnić się od oryginalnego zapytania. Jest to użyteczne, gdy chce się przechowywać tylko część informacji z każdego obiektu sekwencji. W poniższym przykładzie przyjęto założenie, że obiekt produktu (`p`) zawiera wiele pól i metod, i że możesz jest zainteresowany wyłącznie utworzeniem sekwencji obiektów, które zawierają nazwę produktu i cenę jednostkową.  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 Gdy to zapytanie jest wykonywane, `productInfos` zmienna będzie zawierać sekwencję obiektów, które mogą być udostępniane w `foreach` instrukcji, jak pokazano w poniższym przykładzie:  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 Każdy obiekt w nowym typie anonimowym ma dwie właściwości publiczne, które otrzymują takie same nazwy, jak właściwości lub pola w oryginalnym obiekcie. Możesz również zmienić nazwę pola, podczas tworzenia typu anonimowego; w poniższym przykładzie nazwa `UnitPrice` pole `Price`.  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="collection-initializers"></a>Inicjatory kolekcji  
 Inicjatory kolekcji pozwalają określić jedną lub więcej inicjatory elementów podczas inicjowania kolekcji typu, który implementuje <xref:System.Collections.IEnumerable> i ma `Add` z odpowiednim podpisem jako metodę wystąpienia lub metodę rozszerzenia. Inicjatory elementów mogą być wartościami prostymi, wyrażeniami lub inicjatorami obiektów. Za pomocą inicjatora kolekcji nie trzeba określać wielu wywołań `Add` klasy w kodzie źródłowym, ponieważ kompilator sam doda te wywołania.  
  
 W poniższych przykładach pokazano dwa proste inicjatory kolekcji:  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 Następujący inicjator kolekcji używa inicjatorów obiektów w celu zainicjowania obiektów klasy `Cat` klasy zdefiniowanej w poprzednim przykładzie. Należy zauważyć, że poszczególne inicjatory obiektów są umieszczone w nawiasach klamrowych i rozdzielone przecinkami.  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 Można określić [null](../../../csharp/language-reference/keywords/null.md) jako element w inicjatorze kolekcji Jeśli kolekcji `Add` zezwala na to metoda.  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 Można określić indeksowane elementów, jeśli kolekcja obsługuje indeksowanie.  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="examples"></a>Przykłady

 Poniższy przykład łączy koncepcji inicjatory obiektów i kolekcji.

 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
 
 Pokazano w poniższym przykładzie obiekt, który implementuje <xref:System.Collections.IEnumerable> zawierający `Add` metody z wieloma parametrami umożliwia inicjatory kolekcji z wieloma elementami każdego elementu na liście odpowiadający podpis `Add` metody. 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 `Add` można użyć metody `params` — słowo kluczowe, aby móc zmienną liczbę argumentów, jak pokazano w poniższym przykładzie. W tym przykładzie pokazano niestandardową implementację indeksatora również zainicjować kolekcji za pomocą indeksów.
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
