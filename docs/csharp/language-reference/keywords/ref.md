---
title: "ref (odwołanie w C#)"
ms.date: 05/30/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0be0eee67b507e2a209c9caaa3eb14cc60e8a763
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ref-c-reference"></a>ref (odwołanie w C#)

`ref` — Słowo kluczowe wskazuje wartość, która jest przekazywana przez odwołanie. Jest on używany w trzech różnych kontekstach: 

- W podpisie metody i w wywołaniu metody, przekazując argument do metody przez odwołanie. Zobacz [przekazywanie argumentów poprzez odwołanie](#passing-an-argument-by-reference) Aby uzyskać więcej informacji.

- W podpisie metody, aby zwrócić wartość do obiektu wywołującego przez odwołanie. Zobacz [odwołanie zwracane wartości](#reference-return-values) Aby uzyskać więcej informacji.

- W treści elementu członkowskiego, aby wskazać, że odwołanie do wartości zwracanej jest przechowywany lokalnie jako odwołanie do wywołującego zamierza zmodyfikować. Zobacz [zmiennych lokalnych Ref](#ref-locals) Aby uzyskać więcej informacji.

## <a name="passing-an-argument-by-reference"></a>Przekazywanie argumentów poprzez odwołanie

W przypadku używania w liście parametrów metody, `ref` — słowo kluczowe wskazuje, że argument jest przekazywany przez odwołanie, nie przez wartość. Przekazywanie poprzez odwołanie powoduje, że każda zmiana argumentu w metodzie wywołane znajduje odzwierciedlenie w metody wywołującej. Na przykład jeśli wywołujący wyrażenie lokalnej zmiennej lub wyrażenie dostępu do elementu tablicy i wywołana metoda zastępuje obiekt, do którego odwołuje się parametr ref, a następnie lokalnego obiektu wywołującego zmiennej lub element tablicy teraz odwołuje się do nowego obiektu po Metoda zwraca.

> [!NOTE]
>  Nie należy mylić koncepcji przekazywanie poprzez odwołanie z pojęciem typy referencyjne. Dwa pojęcia nie są takie same. Parametr metody mogą być modyfikowane przez `ref` niezależnie od tego, czy jest typem wartości lub typem referencyjnym. Istnieje nie pakującej typu wartości, gdy jest przekazywana przez odwołanie.  

Aby użyć `ref` jawnie należy użyć parametru definicję metody i wywołanie metody `ref` — słowo kluczowe, jak pokazano w poniższym przykładzie.  

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]

Argument przekazywany do `ref` parametr musi zostać zainicjowany przed przekazaniem. To różni się od [limit](out.md) parametrów, argumentów, których nie trzeba jawnie zainicjowane przed są one przekazywane.

Element członkowski klasy nie mogą mieć sygnatur różniących się tylko `ref` i `out`. Błąd kompilatora występuje, jeśli jedyną różnicą między dwoma elementami członkowskimi typu jest, że jedna z nich ma `ref` ma parametr, a druga `out` parametru. Na przykład następujący kod nie kompilacji.  
  
 [!code-csharp[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]
  
 Jednak metod można przeciążać, gdy ma jedną metodę `ref` lub `out` parametr, a druga ma parametr wartość, jak pokazano w poniższym przykładzie.
  
 [!code-csharp[ref-and-overloads](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]
  
 W innych sytuacjach wymagających podpisu dopasowania, takich jak ukrywanie lub przesłonięcie `ref` i `out` stanowią część podpisu i nie pasują do siebie.  
  
 Właściwości nie są zmiennymi. Metody i nie można przekazać do `ref` parametrów.  
  
 Aby uzyskać informacje o sposobie przekazać tablice, zobacz [przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Nie można użyć `ref` i `out` słowa kluczowe dla następujących rodzajów metod:  
  
-   Metody asynchroniczne, które definiują przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.  
  
-   Metody iteracyjne, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.  
  
## <a name="passing-an-argument-by-reference-an-example"></a>Przekazywanie argumentów poprzez odwołanie: przykład

Poprzednich przykładach przekazuj typów wartości przez odwołanie. Można również użyć `ref` — słowo kluczowe do przekazania odwołania typów przez odwołanie. Przekazywanie poprzez odwołanie typu odwołania umożliwia wywołaną metodę zastąpić obiekt, do którego odwołuje się parametr odwołania w wywołującego. Lokalizacja magazynu obiektu jest przekazywany do metody jako wartość parametru odwołania. Wartość w lokalizacji przechowywania parametru (aby wskazywały nowy obiekt), możesz także zmiana lokalizacji przechowywania, do którego odwołuje się element wywołujący. Poniższy przykład przekazuje wystąpienia typu referencyjnego jako `ref` parametru.   
  
 [!code-csharp[ReferencesByRef](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]  

Aby uzyskać więcej informacji na temat przekazywania typów referencyjnych według wartości i według odwołania, zobacz [przekazywanie parametrów typu odwołanie](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Odwołanie do zwracanych wartości

Odwołanie zwracane wartości (lub zwraca ref) to wartości, które metoda zwraca wartość przez odwołanie do obiektu wywołującego. Oznacza to wywołujący może zmodyfikować wartość zwrócona przez metodę, a zmiana ta jest uwzględniana w stan obiektu, który zawiera metodę. 

Odwołanie zwrócić wartość jest definiowana za pomocą `ref` — słowo kluczowe:

- W podpisie metody. Na przykład następujące Określa podpis metody który `GetCurrentPrice` metoda zwraca <xref:System.Decimal> wartość przez odwołanie.

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- Przed każdym `return` instrukcji w metodzie. Na przykład:
 
   ```csharp
   ref return Decimal.Zero;
   ``` 

Aby dla obiekt wywołujący, aby zmodyfikować stan obiektu odwołania zwrócić wartość musi być przechowywany w zmiennej, który jest jawnie zdefiniowany jako [lokalnej typu ref](#ref-locals). 

Na przykład zobacz [A ref zwraca i przykładowe elementy lokalne ref](#a-ref-returns-and-ref-locals-example)

## <a name="ref-locals"></a>Zmienne lokalne REF

Zmienna lokalna ref jest używana do odwoływania się do wartości zwracanych przy użyciu `ref return`.  Zmienna lokalna ref należy zainicjować i przypisane do wartości zwracanej ref. Wszelkie modyfikacje wartość Zmienna lokalna ref są uwzględniane w stan obiektu, którego metoda zwróciła wartość przez odwołanie.

Zdefiniuj zmienna lokalna ref przy użyciu `ref` — słowo kluczowe przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie. 

Na przykład następująca instrukcja definiuje ref wartości lokalnej, który jest zwracany przez metodę o nazwie `GetEstimatedValue`:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Należy pamiętać, że `ref` — słowo kluczowe może być używane w obu miejscach lub kompilator generuje błąd CS8172 "Nie można zainicjować zmiennej dostępnej przez odwołanie o wartości". 
 
## <a name="a-ref-returns-and-ref-locals-example"></a>A przykład zmiennych lokalnych ref i zwraca ref

W poniższym przykładzie zdefiniowano `Book` klasy, która ma dwa <xref:System.String> pól, `Title` i `Author`. Definiuje również `BookCollection` klasa, która zawiera prywatne tablicę `Book` obiektów. Podręcznik poszczególnych obiektów są zwracane przez odwołanie przez wywołanie jego `GetBookByTitle` metody.

[!code-csharp[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#1)]  

Gdy obiekt wywołujący przechowuje wartość zwrócona przez `GetBookByTitle` metodę jako zmiennej lokalnej typu ref, zmiany wywołującego sprawia, że do wartości zwracanej są odzwierciedlane w `BookCollection` obiektu, jak przedstawiono na poniższym przykładzie.

[!code-csharp[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#2)]  

## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Przekazywanie parametrów](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
