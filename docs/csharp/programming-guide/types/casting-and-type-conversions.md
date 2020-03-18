---
title: Konwersje rzutowania i typu - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 252d509617ab5dbc53b282bac52e356396d82fab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711899"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Konwersje rzutowania i typu (Przewodnik programowania Języka C#)

Ponieważ C# jest statycznie typizowane w czasie kompilacji, po zmiennej jest zadeklarowany, nie można zadeklarować ponownie lub przypisać wartość innego typu, chyba że ten typ jest niejawnie konwertowalne do typu zmiennej. Na przykład `string` nie można niejawnie `int`przekonwertować na . W związku z `i` tym `int`po zadeklarowaniu jako , nie można przypisać ciąg "Hello" do niego, jak pokazano następujący kod:
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 Jednak czasami może być konieczne skopiowanie wartości do parametru zmiennej lub metody innego typu. Na przykład może istnieć zmienna całkowita, którą należy przekazać do `double`metody, której parametr jest wpisany jako . Lub może być konieczne przypisanie zmiennej klasy do zmiennej typu interfejsu. Tego rodzaju operacje są nazywane *konwersjami typu*. W języku C#można wykonywać następujące rodzaje konwersji:  
  
- **Konwersje niejawne:** Nie jest wymagana specjalna składnia, ponieważ konwersja jest bezpieczna dla typu i żadne dane nie zostaną utracone. Przykłady obejmują konwersje z mniejszych do większych typów całki i konwersje z klas pochodnych do klas podstawowych.  
  
- **Jawne konwersje (rzutowania):** Konwersje jawne wymagają [ `()`operatora rzutowania ](../../language-reference/operators/type-testing-and-cast.md#cast-operator-). Rzutowanie jest wymagane, gdy informacje mogą zostać utracone w konwersji lub gdy konwersja może nie powiedzie się z innych powodów. Typowe przykłady obejmują konwersję numeryczną na typ, który ma mniejszą precyzję lub mniejszy zakres, oraz konwersję wystąpienia klasy podstawowej na klasę pochodną.  
  
- **Konwersje zdefiniowane przez użytkownika**: Konwersje zdefiniowane przez użytkownika są wykonywane za pomocą specjalnych metod, które można zdefiniować, aby umożliwić jawne i niejawne konwersje między typami niestandardowymi, które nie mają relacji klasy podstawowej. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](../../language-reference/operators/user-defined-conversion-operators.md).  
  
- **Konwersje z klasami pomocnika**: Aby przekonwertować między niezgodnymi typami, <xref:System.DateTime?displayProperty=nameWithType> takimi jak liczby całkowite i obiekty, lub <xref:System.BitConverter?displayProperty=nameWithType> ciągami <xref:System.Convert?displayProperty=nameWithType> szesnastkowymi i tablicami bajtów, można użyć klasy, klasy i `Parse` metod wbudowanych typów liczbowych, takich jak <xref:System.Int32.Parse%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Jak przekonwertować tablicę bajtów na int](./how-to-convert-a-byte-array-to-an-int.md), [Jak przekonwertować ciąg na liczbę](./how-to-convert-a-string-to-a-number.md)i Jak [przekonwertować między ciągami szesnastkowymi a typami liczbowymi](./how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
  
## <a name="implicit-conversions"></a>Konwersje niejawne

 W przypadku wbudowanych typów liczbowych można spożyć konwersję, gdy wartość, która ma być przechowywana, może zmieścić się w zmiennej bez obcinania lub zaokrąglania. W przypadku typów całkowitych oznacza to, że zakres typu źródłowego jest właściwym podzbiorem zakresu dla typu docelowego. Na przykład zmienna typu [long](../../language-reference/builtin-types/integral-numeric-types.md) (64-bitowa liczba całkowita) może przechowywać dowolną wartość, którą może przechowywać [int](../../language-reference/builtin-types/integral-numeric-types.md) (32-bitowa liczba całkowita). W poniższym przykładzie kompilator niejawnie `num` konwertuje `long` wartość po prawej `bigNum`stronie na typ przed przypisaniem go do .  
  
 [!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]  
  
 Aby uzyskać pełną listę wszystkich niejawnych konwersji liczbowych, zobacz [niejawnych konwersji liczbowych](../../language-reference/builtin-types/numeric-conversions.md#implicit-numeric-conversions) sekcji [wbudowane konwersje liczbowe](../../language-reference/builtin-types/numeric-conversions.md) artykułu.
  
 Dla typów odwołań niejawna konwersja zawsze istnieje z klasy do jednej z jej bezpośrednich lub pośrednich klas podstawowych lub interfejsów. Nie jest konieczna specjalna składnia, ponieważ klasa pochodna zawsze zawiera wszystkie elementy członkowskie klasy podstawowej.  
  
```csharp
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Jawne konwersje

 Jednak jeśli konwersja nie może być wykonane bez ryzyka utraty informacji, kompilator wymaga wykonania jawnej konwersji, która jest nazywana *rzutowania*. Rzutowanie jest sposobem jawnie informowania kompilatora, który ma dokonać konwersji i że jesteś świadomy, że może wystąpić utrata danych. Aby wykonać rzutowanie, określ typ, który jest rzutowany w nawiasach przed wartością lub zmienną, która ma zostać przekonwertowana. Poniższy program rzuca [podwójne](../../language-reference/builtin-types/floating-point-numeric-types.md) [do int](../../language-reference/builtin-types/integral-numeric-types.md). Program nie będzie kompilowany bez obsady.  
  
 [!code-csharp[csProgGuideTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#2)]  
  
 Aby uzyskać pełną listę obsługiwanych jawnych konwersji liczbowych, zobacz sekcję [Jawne konwersje liczbowe](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) w artykule [Wbudowane konwersje liczbowe.](../../language-reference/builtin-types/numeric-conversions.md)
  
 W przypadku typów odwołań wymagane jest jawne rzutowania, jeśli trzeba przekonwertować z typu podstawowego na typ pochodny:  
  
```csharp  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 Operacja rzutowania między typami odwołań nie zmienia typu czasu wykonywania obiektu źródłowego; zmienia tylko typ wartości, która jest używana jako odwołanie do tego obiektu. Aby uzyskać więcej informacji, zobacz [Polimorfizm](../classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Wpisywanie wyjątków konwersji w czasie wykonywania

 W niektórych konwersjach typu odwołania kompilator nie może określić, czy rzutowania będzie prawidłowy. Jest możliwe dla operacji rzutowania, który kompiluje poprawnie zakończyć się niepowodzeniem w czasie wykonywania. Jak pokazano w poniższym przykładzie typu rzutnie, <xref:System.InvalidCastException> który kończy się niepowodzeniem w czasie wykonywania spowoduje, że zostanie wyrzucone.  
  
 [!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]  
  
 C# udostępnia [is](../../language-reference/operators/type-testing-and-cast.md#is-operator) operator, aby umożliwić testowanie zgodności przed faktycznie wykonywania rzutowania. Aby uzyskać więcej informacji, zobacz [Jak bezpiecznie rzutować przy użyciu dopasowania wzorców i jak i jest operatory](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).  
  
## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [konwersje](~/_csharplang/spec/conversions.md) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Typy](./index.md)
- [() operator odlewania](../../language-reference/operators/type-testing-and-cast.md#cast-operator-)
- [Operatory konwersji zdefiniowane przez użytkownika](../../language-reference/operators/user-defined-conversion-operators.md)
- [Konwersja uogólnionych typów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))
- [Konwertowanie ciągu na liczbę](./how-to-convert-a-string-to-a-number.md)
