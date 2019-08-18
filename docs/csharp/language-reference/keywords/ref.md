---
title: ref — słowo C# kluczowe — odwołanie
ms.custom: seodec18
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: f11137b3c13bb9e8670c4df25fedf3251724a088
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566896"
---
# <a name="ref-c-reference"></a>ref (odwołanie w C#)

`ref` Słowo kluczowe wskazuje wartość, która jest przenoszona przez odwołanie. Jest on używany w czterech różnych kontekstach:

- W sygnaturze metody i w wywołaniu metody, aby przekazać argument do metody przez odwołanie. Aby uzyskać więcej informacji, zobacz [przekazywanie argumentu przez odwołanie](#passing-an-argument-by-reference).
- W podpisie metody, aby zwrócić wartość do obiektu wywołującego przez odwołanie. Aby uzyskać więcej informacji, zobacz [odwołania do zwracanych wartości](#reference-return-values).
- W treści elementu członkowskiego, aby wskazać, że wartość zwracana przez odwołanie jest przechowywana lokalnie jako odwołanie, które obiekt wywołujący zamierza zmodyfikować lub ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie. Aby uzyskać więcej informacji, zobacz [odwołania lokalne](#ref-locals).
- W deklaracji do `ref struct` deklarowania lub `readonly ref struct`. `struct` Aby uzyskać więcej informacji, zobacz [typy struktury ref](#ref-struct-types).

## <a name="passing-an-argument-by-reference"></a>Przekazywanie argumentu przez odwołanie

W przypadku użycia na liście `ref` parametrów metody słowo kluczowe wskazuje, że argument jest przenoszona przez odwołanie, a nie przez wartość. `ref` Słowo kluczowe powoduje, że parametr formalny jest aliasem dla argumentu, który musi być zmienną. Innymi słowy, każda operacja na parametrze jest wykonywana na argumencie. Na przykład, jeśli obiekt wywołujący przekazuje wyrażenie zmiennej lokalnej lub wyrażenie dostępu do elementu tablicy, a wywoływana metoda zastępuje obiekt, do którego odwołuje się parametr ref, wówczas zmienna lokalna obiektu wywołującego lub element array odwołuje się teraz do nowego obiektu, gdy Zwraca metodę.

> [!NOTE]
> Nie należy mylić koncepcji przekazywania przez odwołanie z koncepcją typów referencyjnych. Te dwa koncepcje nie są takie same. Parametr metody można zmodyfikować, `ref` niezależnie od tego, czy jest to typ wartości, czy też typ referencyjny. Nie istnieje opakowanie typu wartości, gdy jest ono przesyłane przez odwołanie.  

Aby użyć `ref` parametru, zarówno definicja metody, jak i Metoda wywołująca muszą jawnie `ref` użyć słowa kluczowego, jak pokazano w poniższym przykładzie.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Argument, który jest przesyłany do `ref` parametru `in` lub musi zostać zainicjowany przed jego przekazaniem. Różni się to od parametrów [out](out-parameter-modifier.md) , których argumenty nie muszą być jawnie inicjowane przed ich przekazaniem.

Elementy członkowskie klasy nie mogą mieć sygnatur, które różnią `ref`się `in`tylko przez `out`, lub. Błąd kompilatora występuje `out`, jeśli jedyną różnicą między dwoma elementami członkowskimi tego typu jest, że jeden z nich `ref` ma parametr, a drugi ma parametr, `in` lub. Poniższy kod, na przykład, nie kompiluje.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Jednakże metody mogą być przeciążone, gdy jedna metoda ma `ref`parametr `in`,, `out` lub, a drugi ma parametr value, jak pokazano w poniższym przykładzie.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 W innych sytuacjach, które wymagają dopasowania podpisu, takich jak ukrywanie lub zastępowanie `ref`, `in`, `out` , i są częścią podpisu i nie pasują do siebie nawzajem.  
  
 Właściwości nie są zmiennymi. Są to metody i nie można ich przekazywać `ref` do parametrów.  
  
 Nie można używać `ref`słów kluczowych `in`, i `out` dla następujących rodzajów metod:  
  
- Metody asynchroniczne zdefiniowane za pomocą modyfikatora [Async](async.md) .  
- Metody iteratorów, które zawierają instrukcję [yield return](yield.md) lub `yield break` .  

## <a name="passing-an-argument-by-reference-an-example"></a>Przekazywanie argumentu przez odwołanie: Przykład

Poprzednie przykłady przechodzą typy wartości według odwołania. Możesz również użyć słowa kluczowego, `ref` aby przekazać typy odwołań przez odwołanie. Przekazywanie typu referencyjnego przez odwołanie włącza wywoływaną metodę, aby zastąpić obiekt, do którego odwołuje się parametr Reference w wywołującym. Lokalizacja przechowywania obiektu jest przenoszona do metody jako wartość parametru Reference. Jeśli zmienisz wartość w lokalizacji magazynu parametru (w celu wskazywania nowego obiektu), zmienisz również lokalizację magazynu, do którego odwołuje się obiekt wywołujący. Poniższy przykład przekazuje wystąpienie typu odwołania jako `ref` parametr.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Aby uzyskać więcej informacji na temat przekazywania typów odwołań według wartości i według odwołania, zobacz [przekazywanie parametrów typu odwołania](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Odwoływanie się do zwracanych wartości

Wartości zwracane przez odwołanie (lub zwroty odwołań) to wartości, które Metoda zwraca przez odwołanie do obiektu wywołującego. Oznacza to, że obiekt wywołujący może zmodyfikować wartość zwróconą przez metodę, a ta zmiana jest odzwierciedlona w stanie obiektu, który zawiera metodę.

Wartość zwracana przez odwołanie jest definiowana za pomocą `ref` słowa kluczowego:

- W podpisie metody. Na przykład następująca sygnatura metody wskazuje, że `GetCurrentPrice` Metoda <xref:System.Decimal> zwraca wartość przez odwołanie.

```csharp
public ref decimal GetCurrentPrice()
```

- Między tokenem i zmienną zwróconą `return` w instrukcji w metodzie. `return` Na przykład:

```csharp
return ref DecimalArray[0];
```

Aby obiekt wywołujący zmodyfikował stan obiektu, wartość zwracana odwołania musi być przechowywana w zmiennej, która jest jawnie zdefiniowana jako [lokalna jako ref](#ref-locals).

Wywołana metoda może również deklarować wartość zwracaną jako `ref readonly` zwracającą wartość przez odwołanie i wymusić, że wywoływany kod nie może zmodyfikować zwracanej wartości. Metoda wywołująca może uniknąć kopiowania zwracanej wartości przez zapisanie wartości w lokalnej zmiennej [ref ReadOnly](#ref-readonly-locals) .

Aby zapoznać się z przykładem, zobacz [przykład ref Returns i ref locales](#a-ref-returns-and-ref-locals-example).

## <a name="ref-locals"></a>Odwołania lokalne

Referencyjna zmienna lokalna służy do odwoływania się do wartości zwracanych przy użyciu `return ref`. Nie można zainicjować zmiennej lokalnej ref do wartości zwracanej niebędącej odwołaniem. Innymi słowy, prawa strona inicjowania musi być odwołaniem. Wszelkie modyfikacje wartości lokalnego elementu ref są odzwierciedlane w stanie obiektu, którego Metoda zwróciła wartość przez odwołanie.

Można zdefiniować odwołanie lokalne przy użyciu `ref` słowa kluczowego przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie.

Na przykład poniższa instrukcja definiuje wartość lokalną ref zwracaną przez metodę o nazwie `GetEstimatedValue`:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Możesz uzyskać dostęp do wartości przez odwołanie w ten sam sposób. W niektórych przypadkach uzyskanie dostępu do wartości przez odwołanie zwiększa wydajność poprzez uniknięcie potencjalnie kosztownej operacji kopiowania. Na przykład poniższa instrukcja pokazuje, jak jedna z nich może definiować wartość lokalna ref, która jest używana do odwoływania się do wartości.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Należy zauważyć, że w obu `ref` przykładach słowo kluczowe musi być używane w obu miejscach lub kompilator generuje błąd CS8172, "nie można zainicjować zmiennej przez odwołanie za pomocą wartości".

Począwszy od C# 7,3, zmienna `foreach` iteracji instrukcji może być lokalna lokalną lub ref tylko do odczytu zmienna lokalna. Aby uzyskać więcej informacji, zobacz artykuł [instrukcji foreach](foreach-in.md) .

## <a name="ref-readonly-locals"></a>Odwołania do elementów lokalnych ReadOnly

Wartość Ref Local ReadOnly jest używana do odwoływania się do wartości zwracanych przez metodę lub właściwość `ref readonly` , która ma w jej `return ref`podpisie i używa. Zmienna łączy właściwości `ref` zmiennej lokalnej ze `readonly` zmienną: jest to alias do magazynu, do którego jest przypisany, i nie może być modyfikowany. `ref readonly` 

## <a name="a-ref-returns-and-ref-locals-example"></a>Przykład odwołania ref i lokalne odwołania ref

W poniższym przykładzie zdefiniowano `Book` klasę, która ma <xref:System.String> dwa pola `Title` i `Author`. Definiuje `BookCollection` również klasę, która zawiera prywatną `Book` tablicę obiektów. Poszczególne obiekty książek są zwracane przez odwołanie poprzez wywołanie `GetBookByTitle` metody.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Gdy obiekt wywołujący przechowuje wartość zwróconą przez `GetBookByTitle` metodę jako odwołanie lokalne, zmiany, które obiekt wywołujący wprowadza do wartości zwracanej, są odzwierciedlone `BookCollection` w obiekcie, jak pokazano w poniższym przykładzie.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a>Typy struktur ref

Dodanie modyfikatora `struct` do deklaracji definiuje, że wystąpienia tego typu muszą mieć przydzieloną stos. `ref` Innymi słowy, wystąpienia tych typów nigdy nie mogą być tworzone na stercie jako element członkowski innej klasy. Główną motywacją tej funkcji były <xref:System.Span%601> i powiązane struktury.

Celem zachowania `ref struct` typu jako zmiennej przydzieloną stosowo wprowadzono kilka reguł, które kompilator wymusza dla wszystkich `ref struct` typów.

- Nie można Box a `ref struct`. Nie można przypisać `ref struct` typu do zmiennej typu `object`, `dynamic`lub dowolnego typu interfejsu.
- `ref struct`typy nie mogą implementować interfejsów.
- Nie można zadeklarować `ref struct` jako elementu członkowskiego pola klasy lub normalnej struktury. Obejmuje to deklarowanie automatycznie zaimplementowanej właściwości, co powoduje utworzenie pola zapasowego wygenerowanego przez kompilator. 
- Nie można zadeklarować zmiennych lokalnych, `ref struct` które są typami w metodach asynchronicznych. Można je zadeklarować w metodach synchronicznych <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> które `Task`zwracają lub tak jak typy.
- Nie można zadeklarować `ref struct` zmiennych lokalnych w iteratorach.
- Nie można przechwytywać `ref struct` zmiennych w wyrażeniach lambda ani lokalnych funkcjach.

Te ograniczenia uniemożliwiają przypadkowe użycie programu `ref struct` w sposób, który mógłby wspierać go dla sterty zarządzanej.

Można połączyć modyfikatory, aby zadeklarować strukturę jako `readonly ref`. A `readonly ref struct` obejmuje zalety i `ref struct` ograniczenia deklaracji i `readonly struct` .

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
