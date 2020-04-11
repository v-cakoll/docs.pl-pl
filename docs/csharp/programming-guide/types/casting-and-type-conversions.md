---
title: Odlewanie i konwersje typu - Przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: ae8f18deff5e96d7e475df8814ad64b38d14d585
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121390"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Rzutowanie i konwersje typu (Przewodnik programowania języka C#)

Ponieważ C# jest statycznie typowane w czasie kompilacji, po zadeklarowaniu zmiennej, nie można zadeklarować ponownie lub przypisać wartość innego typu, chyba że ten typ jest niejawnie konwertowane do typu zmiennej. Na przykład `string` nie można niejawnie `int`przekonwertować na . W związku z `i` tym `int`po zadeklarowaniu jako , nie można przypisać ciąg "Hello" do niego, jak pokazano w następującym kodzie:
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 Jednak czasami może być konieczne skopiowanie wartości do zmiennej lub parametru metody innego typu. Na przykład może mieć zmienną całkowitą, która musi przejść do metody, `double`której parametr jest wpisany jako . Lub może być konieczne przypisanie zmiennej klasy do zmiennej typu interfejsu. Tego rodzaju operacje są nazywane *konwersjami typu*. W języku C# można wykonać następujące rodzaje konwersji:  
  
- **Konwersje niejawne:** Nie jest wymagana specjalna składnia, ponieważ konwersja jest bezpieczna i żadne dane nie zostaną utracone. Przykłady obejmują konwersje z mniejszych do większych typów całkowitych i konwersje z klas pochodnych do klas podstawowych.  
  
- **Jawne konwersje (rzuty)**: Jawne konwersje wymagają [wyrażenia rzutowego](../../language-reference/operators/type-testing-and-cast.md#cast-expression). Rzutowanie jest wymagane, gdy informacje mogą zostać utracone podczas konwersji lub gdy konwersja może się nie powieść z innych powodów. Typowe przykłady obejmują konwersji numerycznej do typu, który ma mniejszą precyzję lub mniejszy zakres i konwersji wystąpienia klasy podstawowej do klasy pochodnej.  
  
- **Konwersje zdefiniowane przez użytkownika:** Konwersje zdefiniowane przez użytkownika są wykonywane za pomocą specjalnych metod, które można zdefiniować, aby włączyć jawne i niejawne konwersje między typami niestandardowymi, które nie mają relacji klasy podstawowej-pochodnej. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](../../language-reference/operators/user-defined-conversion-operators.md).  
  
- **Konwersje z klasami pomocnika:** Aby konwertować między typami <xref:System.DateTime?displayProperty=nameWithType> niezgodnymi, takimi jak liczby całkowite i obiekty lub ciągi <xref:System.BitConverter?displayProperty=nameWithType> szesnastkowe i tablice bajtowe, można użyć klasy, <xref:System.Convert?displayProperty=nameWithType> klasy i `Parse` metod wbudowanych typów liczbowych, takich jak <xref:System.Int32.Parse%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Jak konwertować tablicę bajtów na int](./how-to-convert-a-byte-array-to-an-int.md), [Jak przekonwertować ciąg na liczbę](./how-to-convert-a-string-to-a-number.md)i Jak [konwertować ciągi szesnastkowe i typy liczbowe.](./how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
  
## <a name="implicit-conversions"></a>Konwersje niejawne

 Dla wbudowanych typów liczbowych niejawna konwersja może być wykonana, gdy wartość do przechowywania może zmieścić się w zmiennej bez obcinania lub zaokrąglania. Dla typów całkowitych oznacza to, że zakres typu źródłowego jest odpowiednim podzbiorem zakresu dla typu docelowego. Na przykład zmienna typu [long](../../language-reference/builtin-types/integral-numeric-types.md) (64-bitowa liczba całkowita) może przechowywać dowolną wartość, którą może przechowywać [int](../../language-reference/builtin-types/integral-numeric-types.md) (32-bitowa liczba całkowita). W poniższym przykładzie kompilator niejawnie `num` konwertuje wartość `long` po prawej `bigNum`stronie na typ przed przypisaniem go do .  
  
 [!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]  
  
 Aby uzyskać pełną listę wszystkich niejawnych konwersji liczbowych, zobacz sekcję [Niejawne konwersje numeryczne](../../language-reference/builtin-types/numeric-conversions.md#implicit-numeric-conversions) [w artykule Wbudowane konwersje numeryczne.](../../language-reference/builtin-types/numeric-conversions.md)
  
 Dla typów odwołań niejawna konwersja zawsze istnieje z klasy do jednej z jego bezpośrednich lub pośrednich klas podstawowych lub interfejsów. Nie jest konieczna specjalna składnia, ponieważ klasa pochodna zawsze zawiera wszystkie elementy członkowskie klasy podstawowej.  
  
```csharp
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Konwersje jawne

 Jeśli jednak konwersja nie może zostać dokonana bez ryzyka utraty informacji, kompilator wymaga wykonania jawnej konwersji, która jest nazywana *rzutowania*. Rzutowanie jest sposobem jawnie informowania kompilatora, że zamierzasz dokonać konwersji i że jesteś świadomy, że może wystąpić utrata danych. Aby wykonać rzutowanie, należy określić typ, na który rzutowane są rzutowane w nawiasach przed wartością lub zmienną, która ma zostać przekonwertowana. Poniższy program rzuca [podwójne](../../language-reference/builtin-types/floating-point-numeric-types.md) do [int](../../language-reference/builtin-types/integral-numeric-types.md). Program nie będzie kompilować bez obsady.  
  
 [!code-csharp[csProgGuideTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#2)]  
  
 Aby uzyskać pełną listę obsługiwanych jawnych konwersji liczbowych, zobacz [jawne konwersje numeryczne](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) sekcji [wbudowane konwersje numeryczne](../../language-reference/builtin-types/numeric-conversions.md) artykułu.
  
 W przypadku typów odwołań jawne rzutowanie jest wymagane, jeśli trzeba przekonwertować z typu podstawowego na typ pochodny:  
  
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
  
 Operacja rzutowa między typami odwołań nie zmienia typu wykonywania obiektu bazowego; zmienia tylko typ wartości, która jest używana jako odwołanie do tego obiektu. Aby uzyskać więcej informacji, zobacz [Polymorphism](../classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Wpisz wyjątki konwersji w czasie wykonywania

 W niektórych konwersji typu odwołania kompilator nie może określić, czy rzutowanie będzie prawidłowe. Jest możliwe dla operacji rzutowania, który kompiluje poprawnie zakończyć się niepowodzeniem w czasie wykonywania. Jak pokazano w poniższym przykładzie, rzutowania typu, <xref:System.InvalidCastException> który kończy się niepowodzeniem w czasie wykonywania spowoduje, że zostanie rzucony.  
  
 [!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]  
  
 C# zapewnia [operator is,](../../language-reference/operators/type-testing-and-cast.md#is-operator) aby umożliwić testowanie zgodności przed faktycznie wykonywania rzutowanie. Aby uzyskać więcej informacji, zobacz [Jak bezpiecznie rzutować za pomocą dopasowywania wzorców i operatorów as i is](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).  
  
## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Konwersje](~/_csharplang/spec/conversions.md) [w specyfikacji języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [C# Przewodnik programowania](../index.md)
- [Types](./index.md)
- [Wyrażenie rzutowe](../../language-reference/operators/type-testing-and-cast.md#cast-expression)
- [Operatory konwersji zdefiniowane przez użytkownika](../../language-reference/operators/user-defined-conversion-operators.md)
- [Konwersja uogólnionych typów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))
- [Konwertowanie ciągu na liczbę](./how-to-convert-a-string-to-a-number.md)
