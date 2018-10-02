---
title: REF — słowo kluczowe (odwołanie w C#)
ms.date: 03/06/2018
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: e0b82de125246e95d8dce2a7afc20119a8a1fe4f
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027913"
---
# <a name="ref-c-reference"></a>ref (odwołanie w C#)

`ref` — Słowo kluczowe wskazuje wartość informującą który jest przekazywany przez odwołanie. Jest on używany w czterech różnych kontekstach:

- W podpisie metody i w wywołaniu metody, aby przekazać argument do metody przez odwołanie. Zobacz [przekazywaniem argumentu według odwołania](#passing-an-argument-by-reference) Aby uzyskać więcej informacji.
- W podpisie metody, aby zwrócić wartości do obiektu wywołującego przez odwołanie. Zobacz [wartości zwracane odwołanie](#reference-return-values) Aby uzyskać więcej informacji.
- W treści elementu członkowskiego aby wskazać, że zwracana wartość odwołania są przechowywane lokalnie, jako odwołanie do obiektu wywołującego zamierza zmienić lub ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie. Zobacz [zmienne lokalne Ref](#ref-locals) Aby uzyskać więcej informacji.
- W `struct` deklaracji, aby zadeklarować `ref struct` lub `ref readonly struct`. Aby uzyskać więcej informacji, zobacz [odwołania semantyki z typami wartości](../../reference-semantics-with-value-types.md).

## <a name="passing-an-argument-by-reference"></a>Przekazywanie argumentów poprzez odwołanie

Gdy są używane w liście parametrów metody, `ref` słowo kluczowe wskazuje, że argument jest przekazywany przez odwołanie, nie przez wartość. Przekazywanie poprzez odwołanie powoduje, że każda zmiana argumentu w metodzie wywoływanej jest odzwierciedlana w wywoływania metody. Na przykład jeśli obiekt wywołujący przekazuje wyrażenie lokalnej zmiennej lub wyrażenia dostępu do elementu tablicy, a następnie wywoływana metoda zastępuje obiekt, do którego odwołuje się parametr ref, a następnie obiekt wywołujący użytkownika lokalnego zmienna lub element tablicy teraz odwołuje się do nowego obiektu po Metoda zwraca.

> [!NOTE]
> Nie należy mylić koncepcji przekazywanie poprzez odwołanie z pojęciem typy odwołań. Dwoma pojęciami nie są takie same. Parametr metody mogą być modyfikowane przez `ref` niezależnie od tego, czy jest typem wartości lub typem referencyjnym. Istnieje nie opakowanie typu wartości, gdy jest przekazywany przez odwołanie.  

Aby użyć `ref` jawnie użyć parametru, zarówno definicję metody, jak i wywoływania metody `ref` — słowo kluczowe, jak pokazano w poniższym przykładzie.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Argument, który jest przekazywany do `ref` lub `in` parametr musi zostać zainicjowany przed przekazaniem jej. To różni się od [się](out-parameter-modifier.md) parametrów, w której argumenty nie trzeba jawnie zainicjowane przed przekazaniem ich.

Składowa klasy nie może mieć podpisów, które różnią się tylko przez `ref`, `in`, lub `out`. Błąd kompilatora występuje, jeśli jedyną różnicą między dwa elementy członkowskie typu jest, że jedna z nich ma `ref` parametru, a druga ma `out`, lub `in` parametru. Na przykład, poniższy kod nie kompilacji.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Jednak mogą być przeciążone metody, gdy ma jedną z metod `ref`, `in`, lub `out` parametru, a druga ma wartość parametru, jak pokazano w poniższym przykładzie.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 W innych sytuacjach, które wymagają podpis dopasowania, takich jak ukrywać lub zastępowanie `in`, `ref`, i `out` są dostępne w ramach sygnatury i nie pasują do siebie nawzajem.  
  
 Właściwości nie są zmienne. To metody, a nie można przekazać do `ref` parametrów.  
  
 Nie można użyć `ref`, `in`, i `out` słowa kluczowe dla następujących rodzajów metod:  
  
- Metody asynchroniczne, które można zdefiniować przy użyciu [async](async.md) modyfikator.  
- Metody iteratora, które obejmują [yield return](yield.md) lub `yield break` instrukcji.  

## <a name="passing-an-argument-by-reference-an-example"></a>Przekazywanie argumentów poprzez odwołanie: przykład

Poprzednie przykłady przekazuj typów wartości przez odwołanie. Można również użyć `ref` — słowo kluczowe do przekazania odwołania typów przez odwołanie. Przekazywanie typu odwołania przez odwołanie pozwala zastąpić obiekt, do którego odwołuje się parametr odwołania w obiekcie wywołującym metodę o nazwie. Lokalizacja magazynu obiekt jest przekazywany do metody jako wartość parametru odwołania. Jeśli zmienisz wartość w określonej lokalizacji magazynu parametru (aby wskazywały nowy obiekt), możesz również zmienić lokalizację magazynu, do którego odwołuje się obiekt wywołujący. Poniższy przykład przekazuje wystąpienia typu referencyjnego jako `ref` parametru.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Aby uzyskać więcej informacji dotyczących przekazywania typów referencyjnych według wartości i według odwołania, zobacz [przekazywanie parametrów typu odwołanie](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Wartości zwracane odwołanie

Wartości zwracane odwołanie (lub zwracanych ref) są wartościami, które metoda zwraca wartość przez odwołanie do obiektu wywołującego. Oznacza to obiekt wywołujący, można zmodyfikować wartości zwracanej przez metodę, a ta zmiana jest odzwierciedlana w stan obiektu, który zawiera metodę.

Odwołanie zwracają wartość jest definiowana za pomocą `ref` — słowo kluczowe:

- W podpisie metody. Na przykład, następujący podpis metody oznacza, że `GetCurrentPrice` metoda zwraca <xref:System.Decimal> wartość przez odwołanie.

```csharp
public ref decimal GetCurrentPrice()
```

- Między `return` token i zmienna zwracane w `return` instrukcji w metodzie. Na przykład:

```csharp
return ref DecimalArray[0];
```

Aby obiekt wywołujący, aby zmodyfikować stan obiektu, musi być przechowywana wartość do zmiennej, która jest jawnie zdefiniowany jako zwrócić odwołanie [odwołanie lokalne](#ref-locals).

Aby uzyskać przykład, zobacz [A wartości zwracane ref i przykład zmienne lokalne ref](#a-ref-returns-and-ref-locals-example)

## <a name="ref-locals"></a>Zmienne lokalne REF

Zmienna lokalna ref jest używana do odwoływania się do wartości zwracane wartości przy użyciu `return ref`. Zmienna lokalna ref nie można zainicjować do wartości zwracanej-ref. Innymi słowy po prawej stronie inicjowania musi być odwołaniem. Wszelkie modyfikacje, wartość Zmienna lokalna ref są odzwierciedlane w stan obiektu, którego metoda zwróciła wartość przez odwołanie.

Zmienna lokalna ref jest definiowane za pomocą `ref` — słowo kluczowe przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie.

Na przykład następująca instrukcja definiuje lokalna wartość ref, który jest zwracany przez metodę o nazwie `GetEstimatedValue`:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Dostępne wartości przez odwołanie, w taki sam sposób. W niektórych przypadkach uzyskiwanie dostępu do wartości przez odwołanie zwiększa wydajność, unikając operacji kopiowania potencjalnie kosztowne. Na przykład następująca instrukcja pokazuje, jak jeden można zdefiniować wartości lokalnej ref, służący do odwoływać się do wartości.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Należy pamiętać, że w obu przykładach `ref` w obu miejscach, można użyć słowa kluczowego lub kompilator generuje błąd CS8172, "Nie można zainicjować zmiennej przez odwołanie o wartości".

## <a name="a-ref-returns-and-ref-locals-example"></a>Element wartości zwracane ref i przykład zmienne lokalne ref

W poniższym przykładzie zdefiniowano `Book` klasę, która ma dwa <xref:System.String> pól `Title` i `Author`. Umożliwia on również definiowanie `BookCollection` klasa, która zawiera prywatne tablicę `Book` obiektów. Poszczególne książki obiekty są zwracane przez odwołanie, przez wywołanie jego `GetBookByTitle` metody.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Gdy obiekt wywołujący przechowuje wartość zwrócona przez obiekt `GetBookByTitle` zmiany, które sprawia, że obiekt wywołujący na wartość zwracaną metody jako lokalną ref, są odzwierciedlane w `BookCollection` obiektu, co ilustruje poniższy przykład.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Semantyka odwołań z typami wartości](../../reference-semantics-with-value-types.md)  
- [Przekazywanie parametrów](../../programming-guide/classes-and-structs/passing-parameters.md)  
- [Parametry metody](method-parameters.md)  
- [Dokumentacja języka C#](../index.md)  
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
- [Słowa kluczowe języka C#](index.md)