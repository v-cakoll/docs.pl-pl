---
title: REF — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 1faebe2ce1a59798621888e3a518900234720be5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116259"
---
# <a name="ref-c-reference"></a>ref (odwołanie w C#)

`ref` — Słowo kluczowe wskazuje wartość informującą który jest przekazywany przez odwołanie. Jest on używany w czterech różnych kontekstach:

- W podpisie metody i w wywołaniu metody, aby przekazać argument do metody przez odwołanie. Aby uzyskać więcej informacji, zobacz [przekazywaniem argumentu według odwołania](#passing-an-argument-by-reference).
- W podpisie metody, aby zwrócić wartości do obiektu wywołującego przez odwołanie. Aby uzyskać więcej informacji, zobacz [wartości zwracane odwołanie](#reference-return-values).
- W treści elementu członkowskiego aby wskazać, że zwracana wartość odwołania są przechowywane lokalnie, jako odwołanie do obiektu wywołującego zamierza zmienić lub ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie. Aby uzyskać więcej informacji, zobacz [zmienne lokalne Ref](#ref-locals).
- W `struct` deklaracji, aby zadeklarować `ref struct` lub `ref readonly struct`. Aby uzyskać więcej informacji, zobacz [typy struktury ref](#ref-struct-types).

## <a name="passing-an-argument-by-reference"></a>Przekazywanie argumentów poprzez odwołanie

Gdy są używane w liście parametrów metody, `ref` słowo kluczowe wskazuje, że argument jest przekazywany przez odwołanie, nie przez wartość. `ref` — Słowo kluczowe sprawia, że parametr formalny alias dla argumentu, który musi być zmienną. Innymi słowy żadnych operacji na parametr składa się od argumentu. Na przykład jeśli obiekt wywołujący przekazuje wyrażenie lokalnej zmiennej lub wyrażenia dostępu do elementu tablicy, a następnie wywoływana metoda zastępuje obiekt, do którego odwołuje się parametr ref, a następnie obiekt wywołujący użytkownika lokalnego zmienna lub element tablicy teraz odwołuje się do nowego obiektu po Metoda zwraca.

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

## <a name="passing-an-argument-by-reference-an-example"></a>Przekazywanie argumentów poprzez odwołanie: Przykład

Poprzednie przykłady przekazuj typów wartości przez odwołanie. Można również użyć `ref` — słowo kluczowe do przekazania odwołania typów przez odwołanie. Przekazywanie typu odwołania przez odwołanie pozwala zastąpić obiekt, do którego odwołuje się parametr odwołania w obiekcie wywołującym metodę o nazwie. Lokalizacja magazynu obiekt jest przekazywany do metody jako wartość parametru odwołania. Jeśli zmienisz wartość w określonej lokalizacji magazynu parametru (aby wskazywały nowy obiekt), możesz również zmienić lokalizację magazynu, do którego odwołuje się obiekt wywołujący. Poniższy przykład przekazuje wystąpienia typu referencyjnego jako `ref` parametru.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Aby uzyskać więcej informacji dotyczących przekazywania typów referencyjnych według wartości i według odwołania, zobacz [przekazywanie parametrów typu odwołanie](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Odwoływanie się do zwracanych wartości

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

Wywoływana metoda również mogą zadeklarować wartość zwracana jako `ref readonly` zwraca wartość przez odwołanie w celu wymuszenia, aby kod wywołujący nie można zmodyfikować zwracanej wartości. Kopiowanie zwracanego zwracającej dzięki przechowywaniu wartości w lokalnej uniknąć wywoływania metody [ref tylko do odczytu](#ref-readonly-locals) zmiennej.

Aby uzyskać przykład, zobacz [A wartości zwracane ref i przykład zmienne lokalne ref](#a-ref-returns-and-ref-locals-example).

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

Począwszy od C# 7.3, zmiennej iteracji `foreach` instrukcja może być zmienna lokalna ref lub zmiennej lokalnej tylko do odczytu ref. Aby uzyskać więcej informacji, zobacz [Instrukcja foreach](foreach-in.md) artykułu.

## <a name="ref-readonly-locals"></a>Zmienne lokalne REF tylko do odczytu

Odwołanie lokalne tylko do odczytu jest używana do odwoływania się do wartości zwracanych przez metodę lub właściwość, która ma `ref readonly` w jego podpisu i używa `return ref`. A `ref readonly` zmiennej łączy właściwości `ref` zmienna lokalna o `readonly` zmiennej: jest to alias do magazynu jest przypisany do, a nie można modyfikować. 

## <a name="a-ref-returns-and-ref-locals-example"></a>Element wartości zwracane ref i przykład zmienne lokalne ref

W poniższym przykładzie zdefiniowano `Book` klasę, która ma dwa <xref:System.String> pól `Title` i `Author`. Umożliwia on również definiowanie `BookCollection` klasa, która zawiera prywatne tablicę `Book` obiektów. Poszczególne książki obiekty są zwracane przez odwołanie, przez wywołanie jego `GetBookByTitle` metody.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Gdy obiekt wywołujący przechowuje wartość zwrócona przez obiekt `GetBookByTitle` zmiany, które sprawia, że obiekt wywołujący na wartość zwracaną metody jako lokalną ref, są odzwierciedlane w `BookCollection` obiektu, co ilustruje poniższy przykład.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a>Typy struktury REF

Dodawanie `ref` modyfikatora `struct` deklaracja określa, że wystąpienia tego typu musi znajdować się na stosie. Innymi słowy te typy można nigdy nie można tworzyć wystąpień na stosie jest członkiem innej klasy. Główną motywacją do tej funkcji został <xref:System.Span%601> i pokrewne struktury.

Celem zachowywaniu `ref struct` wpisz zmienną przydzielanych ze stosów wprowadza kilka reguł, które kompilator wymusza dla wszystkich `ref struct` typów.

- Nie można polu `ref struct`. Nie można przypisać `ref struct` typ do zmiennej typu `object`, `dynamic`, lub dowolny typ interfejsu.
- `ref struct` typy nie mogą implementować interfejsów.
- Nie można zadeklarować `ref struct` jako członek klasy lub struktury normalny.
- Nie można zadeklarować zmienne lokalne, które są `ref struct` typów w metodach asynchronicznych. Można zadeklarować je metod synchronicznych, które zwracają <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> lub `Task`— takich jak typy.
- Nie można zadeklarować `ref struct` zmiennych lokalnych w iteratorach.
- Nie można dokonać przechwytu `ref struct` zmiennych w wyrażeniach lambda lub funkcji lokalnych.

Te ograniczenia, upewnij się, nie używasz przypadkowo `ref struct` w taki sposób, który można podwyższyć poziom do zarządzanej sterty.

Można połączyć modyfikatorów, aby zadeklarować struktury jako `readonly ref`. A `readonly ref struct` łączy korzyści i ograniczeń dotyczących `ref struct` i `readonly struct` deklaracji.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Pisanie kodu efektywne bezpieczne](../../write-safe-efficient-code.md)
- [Wartości zwracane ref i zmienne lokalne ref](../../programming-guide/classes-and-structs/ref-returns.md)
- [Wyrażenie warunkowe ref](../operators/conditional-operator.md#conditional-ref-expression)
- [operator przypisania REF](../operators/assignment-operator.md#ref-assignment-operator)
- [Przekazywanie parametrów](../../programming-guide/classes-and-structs/passing-parameters.md)
- [Parametry metody](method-parameters.md)
- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
