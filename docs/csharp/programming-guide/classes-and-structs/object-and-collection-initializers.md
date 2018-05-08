---
title: Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: ad8127bfdd7178051077e6f3fe75c777acf5d345
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="object-and-collection-initializers-c-programming-guide"></a>Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)
Inicjatory obiektów umożliwiają przypisywanie wartości do dowolnych dostępnych pól lub właściwości obiektu w czasie jego tworzenia, bez konieczności wywoływania konstruktora, po którym występują wiersze instrukcji przypisania. Składnia inicjatora obiektów umożliwia określenie argumentów dla konstruktora lub pominięcie argumentów (i składni z nawiasami).  Poniższy przykład przedstawia użycie inicjatora obiektów z nazwanym typem `Cat` oraz sposób wywołania konstruktora domyślnego. Zwróć uwagę na użycie właściwości zaimplementowane automatycznie w `Cat` klasy. Aby uzyskać więcej informacji, zobacz [Auto-Implemented właściwości](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
Składnię inicjatory obiektów służy do tworzenia wystąpienia, i po tym nowo utworzony obiekt z jego właściwości przypisane, przypisuje do zmiennej przypisania.
  
## <a name="object-initializers-with-anonymous-types"></a>Inicjatory obiektów z typami anonimowymi  
 Chociaż inicjatory obiektów można używać w dowolnym kontekście, jest szczególnie przydatne w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenia zapytań. Wyrażenia zapytań wykorzystują częste [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), które można zainicjować tylko za pomocą inicjatora obiektów, jak pokazano w poniższych deklaracji.  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 Włącz typy anonimowe `select` w klauzuli [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania wyrażenia do przekształcania obiekty z oryginalnej sekwencji obiektów, których wartość i kształtu mogą się różnić od oryginału. Jest to użyteczne, gdy chce się przechowywać tylko część informacji z każdego obiektu sekwencji. W poniższym przykładzie przyjęto założenie, że obiekt produktu (`p`) zawiera wiele pól i metod, i że interesuje Cię tylko podczas tworzenia sekwencji obiektów, które zawierają nazwę produktu i cenie jednostkowej.  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 Podczas wykonywania tego zapytania `productInfos` zmienna będzie zawierać sekwencji obiektów, które są dostępne w `foreach` instrukcji, jak pokazano w poniższym przykładzie:  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 Każdy obiekt w nowym typie anonimowym ma dwie właściwości publiczne, które otrzymują takie same nazwy, jak właściwości lub pola w oryginalnym obiekcie. Można również zmienić nazwę pola, podczas tworzenia typu anonimowego; Poniższy przykład zmienia nazwę `UnitPrice` do `Price`.  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="object-initializers-with-nullable-types"></a>Inicjatory obiektów z typami zerowalnymi  
 Jest to błąd czasu kompilowania spowodowany użyciem inicjatora obiektów ze strukturą dopuszczającą wartości null.  
  
## <a name="collection-initializers"></a>Inicjatory kolekcji  
 Inicjatory kolekcji pozwalają określić jedną lub więcej inicjatory elementów podczas inicjowania kolekcji typ implementuje ten <xref:System.Collections.IEnumerable> i ma `Add` z odpowiednim podpisem jako metodę wystąpienia lub metody rozszerzenia. Inicjatory elementów mogą być wartościami prostymi, wyrażeniami lub inicjatorami obiektów. Za pomocą inicjatora kolekcji jest konieczne określanie wielu wywołań `Add` klasy w kodzie źródłowym; kompilator dodaje wywołań.  
  
 W poniższych przykładach pokazano dwa proste inicjatory kolekcji:  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 Następujące inicjatora kolekcji używa inicjatory obiektów do zainicjowania obiekty `Cat` klas zdefiniowanych w poprzednim przykładzie. Należy zauważyć, że poszczególne inicjatory obiektów są umieszczone w nawiasach klamrowych i rozdzielone przecinkami.  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 Można określić [null](../../../csharp/language-reference/keywords/null.md) jako elementu inicjatora kolekcji Jeśli kolekcji `Add` pozwala metody.  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 Można określić indeksowane elementy, jeśli kolekcja obsługuje indeksowania.  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="examples"></a>Przykłady

 Poniższy przykład łączy pojęcia inicjatory obiektów i kolekcji.

 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
 
 Pokazano w poniższym przykładzie obiektu, który implementuje <xref:System.Collections.IEnumerable> zawierający `Add` metody z parametrami wielu umożliwia inicjatory kolekcji z wielu elementów dla każdego elementu na liście odpowiadający podpis `Add` metody. 
 
 [!code-csharp[csProgGuideLINQ#84](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_7.cs)]
 
 `Add` można użyć metody `params` — słowo kluczowe podjęcie zmienna liczba argumentów, jak pokazano w poniższym przykładzie. W tym przykładzie przedstawiono implementacja niestandardowa indeksatora, jak również zainicjować kolekcji za pomocą indeksów.
 
 [!code-csharp[csProgGuideLINQ#85](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_8.cs)]
 
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
