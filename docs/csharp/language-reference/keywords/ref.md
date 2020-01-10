---
title: ref — słowo C# kluczowe — odwołanie
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 25c74317ce9033ef10735ee0087f275632b6bd17
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715188"
---
# <a name="ref-c-reference"></a>ref (odwołanie w C#)

Słowo kluczowe `ref` wskazuje wartość, która jest przenoszona przez odwołanie. Jest on używany w czterech różnych kontekstach:

- W sygnaturze metody i w wywołaniu metody, aby przekazać argument do metody przez odwołanie. Aby uzyskać więcej informacji, zobacz [przekazywanie argumentu przez odwołanie](#passing-an-argument-by-reference).
- W podpisie metody, aby zwrócić wartość do obiektu wywołującego przez odwołanie. Aby uzyskać więcej informacji, zobacz [odwołania do zwracanych wartości](#reference-return-values).
- W treści elementu członkowskiego, aby wskazać, że wartość zwracana przez odwołanie jest przechowywana lokalnie jako odwołanie, które obiekt wywołujący zamierza zmodyfikować lub ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie. Aby uzyskać więcej informacji, zobacz [odwołania lokalne](#ref-locals).
- W deklaracji `struct`, aby zadeklarować `ref struct` lub `readonly ref struct`. Aby uzyskać więcej informacji, zobacz [typy struktury ref](#ref-struct-types).

## <a name="passing-an-argument-by-reference"></a>Przekazywanie argumentu przez odwołanie

W przypadku użycia na liście parametrów metody `ref` słowo kluczowe wskazuje, że argument jest przenoszona przez odwołanie, a nie przez wartość. Słowo kluczowe `ref` powoduje, że parametr formalny jest aliasem dla argumentu, który musi być zmienną. Innymi słowy, każda operacja na parametrze jest wykonywana na argumencie. Na przykład, jeśli obiekt wywołujący przekazuje wyrażenie zmiennej lokalnej lub wyrażenie dostępu do elementu tablicy, a wywoływana metoda zastępuje obiekt, do którego odwołuje się parametr ref, wówczas zmienna lokalna obiektu wywołującego lub element array odwołuje się teraz do nowego obiektu, gdy Zwraca metodę.

> [!NOTE]
> Nie należy mylić koncepcji przekazywania przez odwołanie z koncepcją typów referencyjnych. Te dwa koncepcje nie są takie same. Parametr metody może być modyfikowany przez `ref` niezależnie od tego, czy jest to typ wartości czy typ referencyjny. Nie istnieje opakowanie typu wartości, gdy jest ono przesyłane przez odwołanie.  

Aby użyć parametru `ref`, zarówno definicja metody, jak i Metoda wywołująca muszą jawnie użyć słowa kluczowego `ref`, jak pokazano w poniższym przykładzie.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Argument, który jest przesyłany do `ref` lub parametru `in`, musi zostać zainicjowany przed jego przekazaniem. Różni się to od parametrów [out](out-parameter-modifier.md) , których argumenty nie muszą być jawnie inicjowane przed ich przekazaniem.

Elementy członkowskie klasy nie mogą mieć sygnatur, które różnią się tylko `ref`, `in`lub `out`. Błąd kompilatora występuje, jeśli jedyną różnicą między dwoma elementami członkowskimi tego typu jest, że jedna z nich ma parametr `ref`, a drugi ma `out`lub `in` parametr. Poniższy kod, na przykład, nie kompiluje.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Jednakże metody mogą być przeciążone, gdy jedna metoda ma parametr `ref`, `in`lub `out`, a drugi ma parametr value, jak pokazano w poniższym przykładzie.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 W innych sytuacjach, które wymagają dopasowania podpisu, takich jak ukrywanie lub zastępowanie, `in`, `ref`i `out` są częścią podpisu i nie pasują do siebie nawzajem.  
  
 Właściwości nie są zmiennymi. Są to metody i nie można ich przekazywać do parametrów `ref`.  
  
 Nie można użyć słów kluczowych `ref`, `in`i `out` dla następujących rodzajów metod:  
  
- Metody asynchroniczne zdefiniowane za pomocą modyfikatora [Async](async.md) .  
- Metody iteratorów, które zawierają instrukcję [yield return](yield.md) lub `yield break`.  

## <a name="passing-an-argument-by-reference-an-example"></a>Przekazywanie argumentu przez odwołanie: przykład

Poprzednie przykłady przechodzą typy wartości według odwołania. Możesz również użyć słowa kluczowego `ref`, aby przekazać typy odwołań przez odwołanie. Przekazywanie typu referencyjnego przez odwołanie włącza wywoływaną metodę, aby zastąpić obiekt, do którego odwołuje się parametr Reference w wywołującym. Lokalizacja przechowywania obiektu jest przenoszona do metody jako wartość parametru Reference. Jeśli zmienisz wartość w lokalizacji magazynu parametru (w celu wskazywania nowego obiektu), zmienisz również lokalizację magazynu, do którego odwołuje się obiekt wywołujący. Poniższy przykład przekazuje wystąpienie typu referencyjnego jako parametr `ref`.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Aby uzyskać więcej informacji na temat przekazywania typów odwołań według wartości i według odwołania, zobacz [przekazywanie parametrów typu odwołania](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Odwoływanie się do zwracanych wartości

Wartości zwracane przez odwołanie (lub zwroty odwołań) to wartości, które Metoda zwraca przez odwołanie do obiektu wywołującego. Oznacza to, że obiekt wywołujący może zmodyfikować wartość zwróconą przez metodę, a ta zmiana jest odzwierciedlona w stanie obiektu, który zawiera metodę.

Wartość zwracana przez odwołanie jest definiowana przy użyciu słowa kluczowego `ref`:

- W podpisie metody. Na przykład następująca sygnatura metody wskazuje, że metoda `GetCurrentPrice` zwraca wartość <xref:System.Decimal> przez odwołanie.

```csharp
public ref decimal GetCurrentPrice()
```

- Między tokenem `return` i zmienną zwróconą w instrukcji `return` w metodzie. Na przykład:

```csharp
return ref DecimalArray[0];
```

Aby obiekt wywołujący zmodyfikował stan obiektu, wartość zwracana odwołania musi być przechowywana w zmiennej, która jest jawnie zdefiniowana jako [lokalna jako ref](#ref-locals).

Wywołana metoda może również deklarować wartość zwracaną jako `ref readonly`, aby zwrócić wartość przez odwołanie, i wymusić, że wywoływany kod nie może zmodyfikować zwracanej wartości. Metoda wywołująca może uniknąć kopiowania zwracanej wartości przez zapisanie wartości w lokalnej zmiennej [ref ReadOnly](#ref-readonly-locals) .

Aby zapoznać się z przykładem, zobacz [przykład ref Returns i ref locales](#a-ref-returns-and-ref-locals-example).

## <a name="ref-locals"></a>Odwołania lokalne

Referencyjna zmienna lokalna służy do odwoływania się do wartości zwracanych przy użyciu `return ref`. Nie można zainicjować zmiennej lokalnej ref do wartości zwracanej niebędącej odwołaniem. Innymi słowy, prawa strona inicjowania musi być odwołaniem. Wszelkie modyfikacje wartości lokalnego elementu ref są odzwierciedlane w stanie obiektu, którego Metoda zwróciła wartość przez odwołanie.

Można zdefiniować odwołanie lokalne przy użyciu słowa kluczowego `ref` przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie.

Na przykład poniższa instrukcja definiuje wartość lokalną ref zwracaną przez metodę o nazwie `GetEstimatedValue`:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Możesz uzyskać dostęp do wartości przez odwołanie w ten sam sposób. W niektórych przypadkach uzyskanie dostępu do wartości przez odwołanie zwiększa wydajność poprzez uniknięcie potencjalnie kosztownej operacji kopiowania. Na przykład poniższa instrukcja pokazuje, jak jedna z nich może definiować wartość lokalna ref, która jest używana do odwoływania się do wartości.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Należy zauważyć, że w obu przykładach słowo kluczowe `ref` musi być używane w obu miejscach lub kompilator generuje błąd CS8172 "nie można zainicjować zmiennej przez odwołanie za pomocą wartości".

Począwszy od C# 7,3, Zmienna iteracji instrukcji `foreach` może być lokalną zmienną lokalną typu ref lub ref tylko do odczytu. Aby uzyskać więcej informacji, zobacz artykuł [instrukcji foreach](foreach-in.md) .

## <a name="ref-readonly-locals"></a>Odwołania do elementów lokalnych ReadOnly

Wartość Ref Local ReadOnly jest używana do odwoływania się do wartości zwracanych przez metodę lub właściwość, która ma `ref readonly` w jej sygnaturze i używa `return ref`. Zmienna `ref readonly` łączy właściwości zmiennej lokalnej `ref` z zmienną `readonly`: jest to alias do magazynu, do którego jest przypisany, i nie można go modyfikować. 

## <a name="a-ref-returns-and-ref-locals-example"></a>Przykład odwołania ref i lokalne odwołania ref

W poniższym przykładzie zdefiniowano klasę `Book`, która ma dwa <xref:System.String> pola, `Title` i `Author`. Definiuje również klasę `BookCollection`, która zawiera prywatną tablicę obiektów `Book`. Poszczególne obiekty książek są zwracane przez odwołanie poprzez wywołanie jego metody `GetBookByTitle`.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Gdy obiekt wywołujący przechowuje wartość zwróconą przez metodę `GetBookByTitle` jako odwołanie lokalne, zmiany, które obiekt wywołujący wprowadza do wartości zwracanej, są odzwierciedlane w obiekcie `BookCollection`, jak pokazano w poniższym przykładzie.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a>Typy struktur ref

Dodanie modyfikatora `ref` do deklaracji `struct` definiuje, że wystąpienia tego typu muszą mieć przydzieloną stos. Innymi słowy, wystąpienia tych typów nigdy nie mogą być tworzone na stercie jako element członkowski innej klasy. Podstawowa motywacja tej funkcji była <xref:System.Span%601> i powiązane struktury.

Celem zachowania typu `ref struct` jako zmiennej przydzieloną stosowo wprowadzono kilka reguł, które kompilator wymusza dla wszystkich typów `ref struct`.

- Nie można Box `ref struct`. Nie można przypisać typu `ref struct` do zmiennej typu `object`, `dynamic`lub dowolnego typu interfejsu.
- typy `ref struct` nie mogą implementować interfejsów.
- Nie można zadeklarować `ref struct` jako elementu członkowskiego pola klasy lub normalnej struktury. Obejmuje to deklarowanie automatycznie zaimplementowanej właściwości, co powoduje utworzenie pola zapasowego wygenerowanego przez kompilator. 
- Nie można zadeklarować zmiennych lokalnych, które są `ref struct` typami w metodach asynchronicznych. Można je zadeklarować w metodach synchronicznych, które zwracają <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> lub `Task`.
- Nie można zadeklarować zmiennych lokalnych `ref struct` w iteratorach.
- Nie można przechwytywać zmiennych `ref struct` w wyrażeniach lambda ani lokalnych funkcjach.

Te ograniczenia uniemożliwiają przypadkowe użycie `ref struct` w sposób, który mógłby wspierać go w zarządzanym stosie.

Można połączyć modyfikatory, aby zadeklarować strukturę jako `readonly ref`. `readonly ref struct` łączy korzyści i ograniczenia `ref struct` i `readonly struct` deklaracji.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Zapisz bezpieczny wydajny kod](../../write-safe-efficient-code.md)
- [Wartości zwracane ref i zmienne lokalne ref](../../programming-guide/classes-and-structs/ref-returns.md)
- [Wyrażenie warunkowe ref](../operators/conditional-operator.md#conditional-ref-expression)
- [operator przypisania ref](../operators/assignment-operator.md#ref-assignment-operator)
- [Przekazywanie parametrów](../../programming-guide/classes-and-structs/passing-parameters.md)
- [Parametry metody](method-parameters.md)
- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
