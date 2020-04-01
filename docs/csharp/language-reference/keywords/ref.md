---
title: ref — słowo kluczowe — odwołanie do języka C#
ms.date: 03/19/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 8d04f888befae2cad815c88a0d27bd836f458c63
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523775"
---
# <a name="ref-c-reference"></a>ref (odwołanie w C#)

Słowo `ref` kluczowe wskazuje wartość, która jest przekazywana przez odwołanie. Jest on używany w czterech różnych kontekstach:

- W podpisie metody i w wywołaniu metody, aby przekazać argument do metody przez odwołanie. Aby uzyskać więcej informacji, zobacz [Przekazywanie argumentu przez odwołanie](#passing-an-argument-by-reference).
- W podpisie metody, aby zwrócić wartość do wywołującego przez odwołanie. Aby uzyskać więcej informacji, zobacz [Odwołanie do wartości zwracanej](#reference-return-values).
- W treści elementu członkowskiego, aby wskazać, że wartość zwracana odwołania jest przechowywana lokalnie jako odwołanie, które obiekt wywołujący zamierza zmodyfikować lub, ogólnie rzecz biorąc, zmienna lokalna uzyskuje dostęp do innej wartości przez odwołanie. Aby uzyskać więcej informacji, zobacz [Ref locals](#ref-locals).
- W `struct` oświadczeniu o `ref struct` zadeklarowaniu a lub . `readonly ref struct` Aby uzyskać więcej informacji, zobacz [typy struktury ref](#ref-struct-types).

## <a name="passing-an-argument-by-reference"></a>Przekazywanie argumentu przez odwołanie

Gdy jest używany na liście parametrów metody, `ref` słowo kluczowe wskazuje, że argument jest przekazywany przez odwołanie, a nie przez wartość. Słowo `ref` kluczowe sprawia, że parametr formalny alias dla argumentu, który musi być zmienną. Innymi słowy, każda operacja na parametr jest na argument. Na przykład jeśli obiekt wywołujący przekazuje wyrażenie zmiennej lokalnej lub wyrażenie dostępu do elementu tablicy, a wywołana metoda zastępuje obiekt, do którego odwołuje się parametr ref, zmienna lokalna wywołującego lub element tablicy odwołuje się teraz do nowego obiektu, gdy metoda zwraca.

> [!NOTE]
> Nie należy mylić pojęcia przekazywania przez odniesienie z pojęciem typów odwołań. Te dwie koncepcje nie są takie same. Parametr metody można modyfikować, `ref` niezależnie od tego, czy jest to typ wartości, czy typ odwołania. Nie ma boksu typu wartości, gdy jest przekazywany przez odwołanie.  

Aby użyć `ref` parametru, zarówno definicji metody i metody `ref` wywołującej należy jawnie użyć słowa kluczowego, jak pokazano w poniższym przykładzie.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Argument, który jest `ref` przekazywany do lub `in` parametru musi być zainicjowany przed przekazaniem. Różni [się](out-parameter-modifier.md) to od out parametrów, których argumenty nie muszą być jawnie zainicjowane przed ich przekazaniem.

Członkowie klasy nie mogą mieć podpisów, `ref`które `in`różnią `out`się tylko przez , lub . Błąd kompilatora występuje, jeśli jedyną różnicą między dwoma `ref` elementami członkowskich typu `out`jest `in` to, że jeden z nich ma parametr, a drugi ma parametr , lub. Poniższy kod, na przykład, nie skompilować.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Jednak metody mogą być przeciążone, `ref`gdy `in`jedna `out` metoda ma , lub parametr, a druga ma parametr wartości, jak pokazano w poniższym przykładzie.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 W innych sytuacjach, które wymagają dopasowywania `in`podpisu, `out` takich jak ukrywanie lub zastępowanie, i `ref`są częścią podpisu i nie pasują do siebie.  
  
 Właściwości nie są zmiennymi. Są to metody i nie `ref` można ich przekazać do parametrów.  
  
 Nie można użyć `ref`programu `in`, `out` i słów kluczowych dla następujących rodzajów metod:  
  
- Metody asynchroniowe, które można zdefiniować za pomocą modyfikatora [asynchronii.](async.md)  
- Metody iteratora, które zawierają `yield break` [zwrotu wydajności](yield.md) lub instrukcji.

Ponadto [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md) mają następujące ograniczenia:

- Nie `out` można użyć słowa kluczowego w pierwszym argumie metody rozszerzenia.
- Nie `ref` można użyć słowa kluczowego w pierwszym argumie metody rozszerzenia, gdy argument nie jest strukturą lub typem rodzajowym, który nie jest ograniczony do struktury.
- Nie `in` można użyć słowa kluczowego, chyba że pierwszy argument jest strukturą. Słowo `in` kluczowe nie może być używane dla dowolnego typu rodzajowego, nawet jeśli jest ograniczona do struktury.

## <a name="passing-an-argument-by-reference-an-example"></a>Przekazywanie argumentu przez odwołanie: Przykład

Poprzednie przykłady przekazać typy wartości przez odwołanie. Za pomocą słowa `ref` kluczowego można również przekazać typy odwołań według odwołań. Przekazywanie typu odwołania przez odwołanie umożliwia wywołaną metodę, aby zastąpić obiekt, do którego odwołuje się parametr odwołania w wywołującym. Lokalizacja przechowywania obiektu jest przekazywana do metody jako wartość parametru referencyjnego. Jeśli zmienisz wartość w lokalizacji przechowywania parametru (aby wskazać nowy obiekt), można również zmienić lokalizację magazynu, do którego odwołuje się obiekt wywołujący. Poniższy przykład przekazuje wystąpienie typu `ref` odwołania jako parametr.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Aby uzyskać więcej informacji na temat przekazywania typów odwołań według wartości i odwołania, zobacz [Przekazywanie parametrów typu odwołania](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Odwoływanie się do zwracanych wartości

Odwołania zwraca wartości (lub ref zwraca) są wartości, które metoda zwraca przez odwołanie do wywołującego. Oznacza to, że obiekt wywołujący można zmodyfikować wartość zwróconą przez metodę, a ta zmiana jest odzwierciedlana w stanie obiektu, który zawiera metodę.

Referencyjna wartość zwracana jest `ref` definiowana przy użyciu słowa kluczowego:

- W podpisie metody. Na przykład następujące podpis metody wskazuje, `GetCurrentPrice` że <xref:System.Decimal> metoda zwraca wartość przez odwołanie.

```csharp
public ref decimal GetCurrentPrice()
```

- Między `return` tokenem a zmienną `return` zwróconą w instrukcji w metodzie. Przykład:

```csharp
return ref DecimalArray[0];
```

Aby obiekt wywołujący zmodyfikował stan obiektu, wartość zwracana odwołanie musi być przechowywana w zmiennej jawnie zdefiniowanej jako [ref local](#ref-locals).

Wywołana metoda może również zadeklarować wartość zwracaną, `ref readonly` aby zwrócić wartość przez odwołanie i wymusić, że kod wywołujący nie może zmodyfikować zwróconą wartość. Wywołanie metoda można uniknąć kopiowania zwracane wartości przez przechowywanie wartości w lokalnym [ref tylko](#ref-readonly-locals) zmiennej.

Na przykład zobacz [A ref zwraca i ref locals przykład](#a-ref-returns-and-ref-locals-example).

## <a name="ref-locals"></a>Ref miejscowi

Zmienna lokalna ref jest używana `return ref`do odwoływania się do wartości zwracanych przy użyciu . Zmiennej lokalnej ref nie można zainicjować do wartości zwracanej non-ref. Innymi słowy, po prawej stronie inicjowania musi być odwołanie. Wszelkie modyfikacje wartości ref local są odzwierciedlane w stanie obiektu, którego metoda zwróciła wartość przez odwołanie.

Można zdefiniować ref lokalnych `ref` przy użyciu słowa kluczowego przed deklaracją zmiennej, a także bezpośrednio przed wywołaniem metody, która zwraca wartość przez odwołanie.

Na przykład następująca instrukcja definiuje wartość lokalną ref, `GetEstimatedValue`która jest zwracana przez metodę o nazwie:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Można uzyskać dostęp do wartości przez odwołanie w ten sam sposób. W niektórych przypadkach dostęp do wartości przez odwołanie zwiększa wydajność, unikając potencjalnie kosztownej operacji kopiowania. Na przykład poniższa instrukcja pokazuje, jak można zdefiniować wartość lokalną ref, która jest używana do odwoływania się do wartości.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Należy zauważyć, że `ref` w obu przykładach słowo kluczowe musi być używane w obu miejscach lub kompilator generuje błąd CS8172, "Nie można zainicjować zmiennej by-reference z wartością."

Począwszy od C# 7.3, zmienną `foreach` iteracji instrukcji może być ref zmiennej lokalnej lub ref readonly zmiennej lokalnej. Aby uzyskać więcej informacji, zobacz artykuł [instrukcji foreach.](foreach-in.md)

Również począwszy od C# 7.3, można ponownie przypisać ref lokalnej lub ref readonly zmiennej lokalnej z [operatorem przypisania ref](../operators/assignment-operator.md#ref-assignment-operator).

## <a name="ref-readonly-locals"></a>Ref czytajnie tylko miejscowi

Ref readonly local jest używany do odwoływania się do `ref readonly` wartości zwracanych `return ref`przez metodę lub właściwość, która ma w podpisie i używa . Zmienna `ref readonly` łączy właściwości zmiennej `ref` lokalnej ze `readonly` zmienną: jest aliasem magazynu, do których jest przypisana i nie można jej zmodyfikować.

## <a name="a-ref-returns-and-ref-locals-example"></a>Ref zwraca i ref przykład lokalnych

Poniższy przykład definiuje `Book` klasę, <xref:System.String> która `Title` ma `Author`dwa pola i . Definiuje również `BookCollection` klasę, która zawiera prywatną tablicę `Book` obiektów. Poszczególne obiekty książki są zwracane `GetBookByTitle` przez odwołanie, wywołując jego metody.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Gdy obiekt wywołujący przechowuje `GetBookByTitle` wartość zwróconą przez metodę jako ref local, zmiany, które `BookCollection` obiekt wywołujący sprawia, że do wartości zwracanej są odzwierciedlane w obiekcie, jak pokazano w poniższym przykładzie.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a>Ref struct typów

Dodanie `ref` modyfikatora `struct` do deklaracji definiuje, że wystąpienia tego typu muszą być przydzielone stos. Innymi słowy wystąpienia tych typów nigdy nie mogą być tworzone na stosie jako członek innej klasy. Główną motywacją dla <xref:System.Span%601> tej funkcji były i powiązane struktury.

Celem zachowania `ref struct` typu jako zmiennej przydzielonej do stosu wprowadza kilka reguł, które kompilator wymusza dla wszystkich `ref struct` typów.

- Nie można pole `ref struct`. Nie można `ref struct` przypisać typu do `object`zmiennej typu `dynamic`lub dowolnego typu interfejsu.
- `ref struct`typy nie można zaimplementować interfejsów.
- Nie można zadeklarować `ref struct` jako członka pola klasy lub normalnej struktury. Obejmuje to deklarowanie właściwości zaimplementowane automatycznie, która tworzy pole zapasowe wygenerowane przez kompilator.
- Nie można zadeklarować zmiennych lokalnych, które są `ref struct` typami w metodach asynchronizacyjnych. Można zadeklarować je w metodach <xref:System.Threading.Tasks.Task>synchronicznych, które zwracają lub <xref:System.Threading.Tasks.Task%601> `Task`-like typów.
- Nie można `ref struct` zadeklarować zmiennych lokalnych w iteratorach.
- Nie można `ref struct` przechwycić zmiennych w wyrażeniach lambda lub funkcji lokalnych.

Te ograniczenia upewnij się, że `ref struct` nie przypadkowo używać w sposób, który może promować go do zarządzanego stosu.

Można połączyć modyfikatory, aby `readonly ref`zadeklarować strukturę jako . A `readonly ref struct` łączy korzyści i ograniczenia `ref struct` `readonly struct` i deklaracje.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Napisz bezpieczny skuteczny kod](../../write-safe-efficient-code.md)
- [Wartości zwracane ref i zmienne lokalne ref](../../programming-guide/classes-and-structs/ref-returns.md)
- [Warunkowe wyrażenie ref](../operators/conditional-operator.md#conditional-ref-expression)
- [Przekazywanie parametrów](../../programming-guide/classes-and-structs/passing-parameters.md)
- [Parametry metody](method-parameters.md)
- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
