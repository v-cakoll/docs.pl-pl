---
title: ref — słowo kluczowe — odwołanie do języka C#
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 05f0bd8566851678203a3f064b96bfff7dee18b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399365"
---
# <a name="ref-c-reference"></a>ref (odwołanie w C#)

Słowo `ref` kluczowe wskazuje wartość, która jest przekazywana przez odwołanie. Jest on używany w czterech różnych kontekstach:

- W podpisie metody i wywołaniu metody, aby przekazać argument do metody przez odwołanie. Aby uzyskać więcej informacji, zobacz [Przekazywanie argumentu przez odwołanie](#passing-an-argument-by-reference).
- W podpisie metody, aby zwrócić wartość do obiektu wywołującego przez odwołanie. Aby uzyskać więcej informacji, zobacz [Wartości zwracane odwołania](#reference-return-values).
- W treści elementu członkowskiego, aby wskazać, że wartość zwracana odwołania jest przechowywana lokalnie jako odwołanie, które obiekt wywołujący zamierza zmodyfikować lub, ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie. Aby uzyskać więcej informacji, zobacz [Ref locals](#ref-locals).
- W `struct` oświadczeniu o `ref struct` zadeklarowanie a lub a `readonly ref struct`. Aby uzyskać więcej informacji, zobacz [typy struktury ref](#ref-struct-types).

## <a name="passing-an-argument-by-reference"></a>Przekazywanie argumentu przez odwołanie

Gdy jest używany na liście parametrów `ref` metody, słowo kluczowe wskazuje, że argument jest przekazywany przez odwołanie, a nie przez wartość. Słowo `ref` kluczowe sprawia, że formalny parametr alias dla argumentu, który musi być zmienna. Innymi słowy, każda operacja na parametr jest na argument. Na przykład jeśli obiekt wywołujący przekazuje wyrażenie zmiennej lokalnej lub wyrażenie dostępu elementu tablicy, a wywoływana metoda zastępuje obiekt, do którego odwołuje się parametr ref, zmienna lokalna obiektu wywołującego lub element tablicy odwołuje się teraz do nowego obiektu, gdy zwraca metodę.

> [!NOTE]
> Nie należy mylić pojęcia przekazywania przez odwołanie z pojęciem typów odwołań. Te dwie koncepcje nie są takie same. Parametr metody można modyfikować `ref` niezależnie od tego, czy jest to typ wartości, czy typ odwołania. Nie ma boksu typu wartości, gdy jest przekazywana przez odwołanie.  

Aby użyć `ref` parametru, zarówno definicji metody, jak i `ref` metody wywołującej należy jawnie użyć słowa kluczowego, jak pokazano w poniższym przykładzie.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Argument, który jest `ref` przekazywany do lub `in` parametr uprzedniego przekazania. Różni się to od [out](out-parameter-modifier.md) parametrów, których argumenty nie muszą być jawnie zainicjowane przed ich przekazaniem.

Członkowie klasy nie mogą mieć podpisów, `ref`które `in`różnią `out`się tylko przez , lub . Błąd kompilatora występuje, jeśli jedyną różnicą między dwoma `ref` członkami typu jest `out`to, że jeden z nich ma parametr, a drugi ma , lub `in` parametr. Poniższy kod, na przykład nie kompiluje.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Jednak metody mogą być przeciążone, `ref`gdy `in`jedna `out` metoda ma , lub parametr, a druga ma parametr value, jak pokazano w poniższym przykładzie.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 W innych sytuacjach, które wymagają dopasowania podpisu, `ref`takich `out` jak ukrywanie lub zastępowanie , `in`i są częścią podpisu i nie pasują do siebie.  
  
 Właściwości nie są zmiennymi. Są to metody i nie `ref` można ich przekazać do parametrów.  
  
 Nie można używać `ref`słów `in` `out` kluczowych i słów kluczowych dla następujących rodzajów metod:  
  
- Metody asynchroniczne, które można zdefiniować za pomocą modyfikatora [asynchronii.](async.md)  
- Metody iterator, które obejmują zwrot `yield break` [uchylić](yield.md) lub instrukcji.  

## <a name="passing-an-argument-by-reference-an-example"></a>Przekazywanie argumentu przez odwołanie: Przykład

Poprzednie przykłady przekazują typy wartości przez odwołanie. Można również użyć `ref` słowa kluczowego, aby przekazać typy odwołań przez odwołanie. Przekazywanie typu odwołania przez odwołanie umożliwia wywoływaną metodę, aby zastąpić obiekt, do którego odwołuje się parametr odwołania w obiekcie wywołującym. Lokalizacja magazynu obiektu jest przekazywana do metody jako wartość parametru referencyjnego. Jeśli zmienisz wartość w lokalizacji magazynu parametru (aby wskazać nowy obiekt), należy również zmienić lokalizację magazynu, do której odwołuje się obiekt wywołujący. Poniższy przykład przekazuje wystąpienie typu odwołania `ref` jako parametr.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Aby uzyskać więcej informacji na temat przekazywania typów odwołań według wartości i przez odwołanie, zobacz [Przekazywanie parametrów typu odwołania](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Odwoływanie się do zwracanych wartości

Wartości zwracane odwołania (lub ref zwraca) są wartości, które zwraca metoda przez odwołanie do obiektu wywołującego. Oznacza to, że obiekt wywołujący można zmodyfikować wartość zwracaną przez metodę, a ta zmiana jest odzwierciedlona w stanie obiektu, który zawiera metodę.

Wartość zwracana odwołania jest definiowana przy użyciu słowa kluczowego: `ref`

- W podpisie metody. Na przykład następujący podpis metody `GetCurrentPrice` wskazuje, <xref:System.Decimal> że metoda zwraca wartość przez odwołanie.

```csharp
public ref decimal GetCurrentPrice()
```

- Między `return` tokenem a zmienną `return` zwróconą w instrukcji w metodzie. Przykład:

```csharp
return ref DecimalArray[0];
```

Aby obiekt wywołujący zmodyfikować stan obiektu, wartość zwracana odwołania musi być przechowywana w zmiennej, która jest jawnie zdefiniowana jako [ref local](#ref-locals).

Wywoływana metoda może również zadeklarować wartość zwracaną, aby `ref readonly` zwrócić wartość przez odwołanie i wymusić, że kod wywołujący nie może zmodyfikować zwracanej wartości. Metoda wywołująca można uniknąć kopiowania zwróconej wartości przez przechowywanie wartości w zmiennej local [ref readonly.](#ref-readonly-locals)

Na przykład zobacz [Ref zwraca i ref locals przykład](#a-ref-returns-and-ref-locals-example).

## <a name="ref-locals"></a>Ref miejscowi

Zmienna lokalna ref jest używana do `return ref`odwoływania się do wartości zwracanych przy użyciu . Zmienna lokalna ref nie może zostać zainicjowana do wartości zwracanej bez ref. Innymi słowy, prawa strona inicjowania musi być odwołaniem. Wszelkie modyfikacje wartości ref local są odzwierciedlane w stanie obiektu, którego metoda zwróciła wartość przez odwołanie.

Można zdefiniować ref local `ref` przy użyciu słowa kluczowego przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie.

Na przykład następująca instrukcja definiuje wartość lokalną ref zwracaną przez metodę o nazwie: `GetEstimatedValue`

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Można uzyskać dostęp do wartości przez odwołanie w ten sam sposób. W niektórych przypadkach dostęp do wartości przez odwołanie zwiększa wydajność, unikając potencjalnie kosztownej operacji kopiowania. Na przykład w poniższej instrukcji pokazano, jak można zdefiniować wartość lokalną ref, która jest używana do odwoływania się do wartości.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Należy zauważyć, że `ref` w obu przykładach słowo kluczowe musi być używane w obu miejscach lub kompilator generuje błąd CS8172, "Nie można zainicjować zmiennej przez odwołanie z wartością."

Począwszy od C# 7.3, zmienna `foreach` iteracji instrukcji może być ref lokalnej lub ref readonly zmiennej lokalnej. Aby uzyskać więcej informacji, zobacz [artykuł foreach instrukcji.](foreach-in.md)

Również począwszy od C# 7.3, można ponownie przypisać ref lokalnej lub ref readonly zmiennej lokalnej z [operatorem przypisania ref](../operators/assignment-operator.md#ref-assignment-operator).

## <a name="ref-readonly-locals"></a>Ref readonly mieszkańców

Ref readonly local jest używany do odwoływania się do `ref readonly` wartości zwracanych `return ref`przez metodę lub właściwość, która ma w swoim podpisie i używa . Zmienna `ref readonly` łączy właściwości zmiennej `ref` lokalnej ze `readonly` zmienną: jest aliasem do magazynu, do których jest przypisany, i nie można go zmodyfikować.

## <a name="a-ref-returns-and-ref-locals-example"></a>Ref zwraca i ref locals przykład

W poniższym przykładzie `Book` zdefiniowano <xref:System.String> klasę, `Author`która ma dwa pola i `Title` . Definiuje również `BookCollection` klasę, która zawiera tablicę prywatną `Book` obiektów. Poszczególne obiekty książki są zwracane `GetBookByTitle` przez odwołanie przez wywołanie jego metody.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Gdy obiekt wywołujący przechowuje wartość `GetBookByTitle` zwracaną przez metodę jako ref local, zmiany wprowadzone przez `BookCollection` obiekt wywołujący do wartości zwracanej są odzwierciedlane w obiekcie, jak pokazano w poniższym przykładzie.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a>Typy struktury ref

Dodawanie `ref` modyfikatora `struct` do deklaracji definiuje, że wystąpienia tego typu muszą być przydzielane na stosie. Innymi słowy wystąpienia tych typów nigdy nie można utworzyć na stercie jako element członkowski innej klasy. Główną motywacją dla <xref:System.Span%601> tej funkcji były i powiązane struktury.

Celem przechowywania `ref struct` typu jako zmiennej przydzielonej do stosu wprowadza `ref struct` kilka reguł, które kompilator wymusza dla wszystkich typów.

- Nie można boksować `ref struct`pliku . Nie można przypisać `ref struct` typu do zmiennej typu `object`lub `dynamic`dowolnego typu interfejsu.
- `ref struct`typy nie można zaimplementować interfejsów.
- Nie można zadeklarować `ref struct` jako członka pola klasy lub normalnej struktury. Obejmuje to deklarowanie właściwości zaimplementowanej automatycznie, która tworzy wygenerowane przez kompilator pole zapasowe.
- Nie można zadeklarować zmiennych lokalnych, które są `ref struct` typami w metodach asynchronicznych. Można zadeklarować je w metodach <xref:System.Threading.Tasks.Task>synchronicznych, które zwracają lub <xref:System.Threading.Tasks.Task%601> `Task`-like typów.
- Nie można `ref struct` zadeklarować zmiennych lokalnych w iteratory.
- Nie można `ref struct` przechwytywać zmiennych w wyrażeniach lambda lub funkcjach lokalnych.

Ograniczenia te zapewniają, że nie `ref struct` przypadkowo użyć w sposób, który może promować go do zarządzanego sterty.

Modyfikatory można łączyć, aby `readonly ref`zadeklarować strukturę jako . A `readonly ref struct` łączy korzyści i `ref struct` ograniczenia `readonly struct` i deklaracje.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Napisz bezpieczny, wydajny kod](../../write-safe-efficient-code.md)
- [Wartości zwracane ref i zmienne lokalne ref](../../programming-guide/classes-and-structs/ref-returns.md)
- [Warunkowe wyrażenie ref](../operators/conditional-operator.md#conditional-ref-expression)
- [Przekazywanie parametrów](../../programming-guide/classes-and-structs/passing-parameters.md)
- [Parametry metody](method-parameters.md)
- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
