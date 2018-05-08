---
title: ref (odwołanie w C#)
ms.date: 03/06/2018
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 8b36f94e9476b857066c292feb9e77e9c2199b7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ref-c-reference"></a>ref (odwołanie w C#)

`ref` — Słowo kluczowe wskazuje wartość, która jest przekazywana przez odwołanie. Jest on używany w trzech różnych kontekstach: 

- W podpisie metody i w wywołaniu metody, przekazując argument do metody przez odwołanie. Zobacz [przekazywanie argumentów poprzez odwołanie](#passing-an-argument-by-reference) Aby uzyskać więcej informacji.

- W podpisie metody, aby zwrócić wartość do obiektu wywołującego przez odwołanie. Zobacz [odwołanie zwracane wartości](#reference-return-values) Aby uzyskać więcej informacji.

- W treści elementu członkowskiego aby wskazać, że odwołanie do wartości zwracanej są przechowywane lokalnie, jako odwołanie do wywołującego zamierza zmienić lub ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie. Zobacz [zmiennych lokalnych Ref](#ref-locals) Aby uzyskać więcej informacji.

## <a name="passing-an-argument-by-reference"></a>Przekazywanie argumentów poprzez odwołanie

W przypadku używania w liście parametrów metody, `ref` — słowo kluczowe wskazuje, że argument jest przekazywany przez odwołanie, nie przez wartość. Przekazywanie poprzez odwołanie powoduje, że każda zmiana argumentu w metodzie wywołane znajduje odzwierciedlenie w metody wywołującej. Na przykład jeśli wywołujący wyrażenie lokalnej zmiennej lub wyrażenie dostępu do elementu tablicy i wywołana metoda zastępuje obiekt, do którego odwołuje się parametr ref, a następnie lokalnego obiektu wywołującego zmiennej lub element tablicy teraz odwołuje się do nowego obiektu po Metoda zwraca.

> [!NOTE]
>  Nie należy mylić koncepcji przekazywanie poprzez odwołanie z pojęciem typy referencyjne. Dwa pojęcia nie są takie same. Parametr metody mogą być modyfikowane przez `ref` niezależnie od tego, czy jest typem wartości lub typem referencyjnym. Istnieje nie pakującej typu wartości, gdy jest przekazywana przez odwołanie.  

Aby użyć `ref` jawnie należy użyć parametru definicję metody i wywołanie metody `ref` — słowo kluczowe, jak pokazano w poniższym przykładzie.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Argument przekazywany do `ref` lub `in` parametr musi zostać zainicjowany przed przekazaniem. To różni się od [limit](out-parameter-modifier.md) parametrów, argumentów, których nie trzeba jawnie zainicjowane przed są one przekazywane.

Element członkowski klasy nie mogą mieć sygnatur różniących się tylko `ref`, `in`, lub `out`. Błąd kompilatora występuje, jeśli jedyną różnicą między dwoma elementami członkowskimi typu jest, że jedna z nich ma `ref` ma parametr, a druga `out`, lub `in` parametru. Na przykład następujący kod nie kompilacji.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
Jednak metod można przeciążać, gdy ma jedną metodę `ref`, `in`, lub `out` parametr, a druga ma parametr wartość, jak pokazano w poniższym przykładzie.
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 W innych sytuacjach wymagających podpisu dopasowania, takich jak ukrywanie lub przesłonięcie `in`, `ref`, i `out` stanowią część podpisu i nie pasują do siebie.  
  
 Właściwości nie są zmiennymi. Metody i nie można przekazać do `ref` parametrów.  
  
 Aby uzyskać informacje o sposobie przekazać tablice, zobacz [przekazywanie tablic za pomocą ref i out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Nie można użyć `ref`, `in`, i `out` słowa kluczowe dla następujących rodzajów metod:  
  
- Metody asynchroniczne, które definiują przy użyciu [async](../../../csharp/language-reference/keywords/async.md) modyfikator.  
- Metody iteracyjne, które obejmują [yield return](../../../csharp/language-reference/keywords/yield.md) lub `yield break` instrukcji.  

## <a name="passing-an-argument-by-reference-an-example"></a>Przekazywanie argumentów poprzez odwołanie: przykład

Poprzednich przykładach przekazuj typów wartości przez odwołanie. Można również użyć `ref` — słowo kluczowe do przekazania odwołania typów przez odwołanie. Przekazywanie poprzez odwołanie typu odwołania umożliwia wywołaną metodę zastąpić obiekt, do którego odwołuje się parametr odwołania w wywołującego. Lokalizacja magazynu obiektu jest przekazywany do metody jako wartość parametru odwołania. Wartość w lokalizacji przechowywania parametru (aby wskazywały nowy obiekt), możesz także zmiana lokalizacji przechowywania, do którego odwołuje się element wywołujący. Poniższy przykład przekazuje wystąpienia typu referencyjnego jako `ref` parametru.   
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Aby uzyskać więcej informacji na temat przekazywania typów referencyjnych według wartości i według odwołania, zobacz [przekazywanie parametrów typu odwołanie](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Odwołanie do zwracanych wartości

Odwołanie zwracane wartości (lub zwraca ref) to wartości, które metoda zwraca wartość przez odwołanie do obiektu wywołującego. Oznacza to wywołujący może zmodyfikować wartość zwrócona przez metodę, a zmiana ta jest uwzględniana w stan obiektu, który zawiera metodę. 

Odwołanie zwrócić wartość jest definiowana za pomocą `ref` — słowo kluczowe:

- W podpisie metody. Na przykład następujące Określa podpis metody który `GetCurrentPrice` metoda zwraca <xref:System.Decimal> wartość przez odwołanie.

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- Między `return` token i zwracany w zmiennej `return` instrukcji w metodzie. Na przykład:
 
   ```csharp
   return ref DecimalArray[0];
   ``` 

Aby dla obiekt wywołujący, aby zmodyfikować stan obiektu odwołania zwrócić wartość musi być przechowywany w zmiennej, który jest jawnie zdefiniowany jako [lokalnej typu ref](#ref-locals). 

Na przykład zobacz [A ref zwraca i przykładowe elementy lokalne ref](#a-ref-returns-and-ref-locals-example)

## <a name="ref-locals"></a>Zmienne lokalne REF

Zmienna lokalna ref jest używana do odwoływania się do wartości zwracanych przy użyciu `return ref`.  Zmienna lokalna ref należy zainicjować i przypisane do wartości zwracanej ref. Wszelkie modyfikacje wartość Zmienna lokalna ref są uwzględniane w stan obiektu, którego metoda zwróciła wartość przez odwołanie.

Zdefiniuj zmienna lokalna ref przy użyciu `ref` — słowo kluczowe przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie. 

Na przykład następująca instrukcja definiuje ref wartości lokalnej, który jest zwracany przez metodę o nazwie `GetEstimatedValue`:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Dostępne wartości przez odwołanie w taki sam sposób. W niektórych przypadkach dostępu do wartość przez odwołanie zwiększa wydajność, unikając operacji kopiowania potencjalnie kosztowne. Na przykład następująca instrukcja pokazuje, jak jedną można zdefiniować wartości lokalnej ref, służący do odwołać się do wartości.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Należy pamiętać, że w obu przykładach `ref` — słowo kluczowe może być używane w obu miejscach lub kompilator generuje błąd CS8172 "Nie można zainicjować zmiennej dostępnej przez odwołanie o wartości". 
 
## <a name="a-ref-returns-and-ref-locals-example"></a>A przykład zmiennych lokalnych ref i zwraca ref

W poniższym przykładzie zdefiniowano `Book` klasy, która ma dwa <xref:System.String> pól, `Title` i `Author`. Definiuje również `BookCollection` klasa, która zawiera prywatne tablicę `Book` obiektów. Podręcznik poszczególnych obiektów są zwracane przez odwołanie przez wywołanie jego `GetBookByTitle` metody.

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Gdy obiekt wywołujący przechowuje wartość zwrócona przez `GetBookByTitle` metodę jako zmiennej lokalnej typu ref, zmiany wywołującego sprawia, że do wartości zwracanej są odzwierciedlane w `BookCollection` obiektu, jak przedstawiono na poniższym przykładzie.

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Przekazywanie parametrów](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
