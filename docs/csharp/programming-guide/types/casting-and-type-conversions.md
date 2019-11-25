---
title: Rzutowanie i konwersje typów C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 33195ef77e2f51e52cd9ed69a11b12bed8d9ead1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969615"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Rzutowanie i konwersje typówC# (Przewodnik programowania)

Ponieważ C# jest statycznie wpisywany w czasie kompilacji, po zadeklarowaniu zmiennej nie można jej ponownie zadeklarować ani przypisać wartości innego typu, chyba że ten typ jest niejawnie konwertowany na typ zmiennej. Na przykład `string` nie może być niejawnie konwertowany na `int`. W związku z tym po zadeklarowaniu `i` jako `int`nie można przypisać do niego ciągu "Hello", ponieważ Poniższy kod ilustruje:
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 Czasami może być konieczne skopiowanie wartości do zmiennej lub parametru metody innego typu. Na przykład może istnieć zmienna typu Integer, która musi zostać przekazana do metody, której parametr został określony jako `double`. Lub może być konieczne przypisanie zmiennej klasy do zmiennej typu interfejsu. Te rodzaje operacji są nazywane *konwersjemi typów*. W C#programie można wykonywać następujące rodzaje konwersji:  
  
- **Konwersje niejawne**: nie jest wymagana żadna specjalna składnia, ponieważ konwersja jest bezpieczna typu i żadne dane nie zostaną utracone. Przykłady obejmują konwersje z mniejszych do większych typów całkowitych i konwersje z klas pochodnych do klas bazowych.  
  
- **Konwersje jawne (rzutowania)** : Konwersje jawne wymagają [`()`operatora rzutowania ](../../language-reference/operators/type-testing-and-cast.md#cast-operator-). Rzutowanie jest wymagane, gdy informacje mogą zostać utracone podczas konwersji lub gdy konwersja może się nie powieść z innych przyczyn. Typowe przykłady obejmują konwersję liczbową do typu, który ma mniejszą precyzję lub mniejszy zakres, i konwersję wystąpienia klasy podstawowej na klasę pochodną.  
  
- **Konwersje zdefiniowane przez użytkownika**: konwersje zdefiniowane przez użytkownika są wykonywane przez specjalne metody, które można zdefiniować, aby włączyć jawne i niejawne konwersje między typami niestandardowymi, które nie mają relacji klasy podstawowej — pochodnej. Aby uzyskać więcej informacji, zobacz [Operatory konwersji zdefiniowane przez użytkownika](../../language-reference/operators/user-defined-conversion-operators.md).  
  
- **Konwersje z klasami pomocniczymi**: aby konwertować między niezgodnymi typami, takimi jak liczby całkowite i obiekty <xref:System.DateTime?displayProperty=nameWithType>, lub ciągi szesnastkowe i tablice bajtowe, można użyć klasy <xref:System.BitConverter?displayProperty=nameWithType>, klasy <xref:System.Convert?displayProperty=nameWithType> oraz metod `Parse` wbudowanych typów liczbowych, takich jak <xref:System.Int32.Parse%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [jak: konwertowanie tablicy bajtów na int](./how-to-convert-a-byte-array-to-an-int.md), [jak: konwertowanie ciągu na liczbę](./how-to-convert-a-string-to-a-number.md)i [instrukcje: konwertowanie między ciągami szesnastkowymi i typami liczbowymi](./how-to-convert-between-hexadecimal-strings-and-numeric-types.md).  
  
## <a name="implicit-conversions"></a>Konwersje niejawne

 W przypadku wbudowanych typów liczbowych można wykonać niejawną konwersję, gdy wartość do zapisania może pasować do zmiennej bez obcinania lub zaokrąglania wartości. W przypadku typów całkowitych oznacza to, że zakres typu źródła jest prawidłowym podzbiorem zakresu dla typu docelowego. Na przykład zmienna typu [Long](../../language-reference/builtin-types/integral-numeric-types.md) (64-bit Integer) może przechowywać dowolną wartość, która może być przechowywana przez [int](../../language-reference/builtin-types/integral-numeric-types.md) (32-bitową liczbę całkowitą). W poniższym przykładzie kompilator niejawnie konwertuje wartość `num` po prawej stronie na typ `long` przed przypisaniem go do `bigNum`.  
  
 [!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]  
  
 Aby zapoznać się z pełną listą wszystkich niejawnych konwersji liczbowych, zobacz sekcję [niejawne konwersje liczbowe](../../language-reference/builtin-types/numeric-conversions.md#implicit-numeric-conversions) w [wbudowanym artykule konwersje numeryczne](../../language-reference/builtin-types/numeric-conversions.md) .
  
 W przypadku typów referencyjnych niejawna konwersja zawsze istnieje z klasy do jednej z jej bezpośrednich lub pośrednich klas podstawowych lub interfejsów. Żadna specjalna składnia nie jest konieczna, ponieważ Klasa pochodna zawsze zawiera wszystkie elementy członkowskie klasy bazowej.  
  
```csharp
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Konwersje jawne

 Jeśli jednak konwersja nie może zostać wykonana bez ryzyka utraty informacji, kompilator wymaga wykonania jawnej konwersji, która jest nazywana *rzutem*. Rzutowanie jest sposobem jawnego informowania kompilatora o planowanym konwersji oraz o tym, że może wystąpić utrata danych. Aby wykonać rzutowanie, określ typ, który jest rzutowany w nawiasy przed wartością lub zmienną do przekonwertowania. Poniższy program rzutuje wartość typu [Double](../../language-reference/builtin-types/floating-point-numeric-types.md) na liczbę [całkowitą.](../../language-reference/builtin-types/integral-numeric-types.md) Program nie zostanie skompilowany bez rzutowania.  
  
 [!code-csharp[csProgGuideTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#2)]  
  
 Aby uzyskać pełną listę obsługiwanych jawnych konwersji liczbowych, zobacz sekcję [jawne konwersje liczbowe](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) w [wbudowanym artykule konwersje numeryczne](../../language-reference/builtin-types/numeric-conversions.md) .
  
 W przypadku typów referencyjnych jawne rzutowanie jest wymagane, jeśli trzeba skonwertować typ podstawowy na typ pochodny:  
  
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
  
 Operacja cast między typami referencyjnymi nie zmienia typu czasu wykonywania obiektu źródłowego; zmienia typ wartości, która jest używana jako odwołanie do tego obiektu. Aby uzyskać więcej informacji, zobacz [polimorfizm](../classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Wyjątki konwersji typów w czasie wykonywania

 W przypadku niektórych konwersji typu odwołania kompilator nie może określić, czy rzutowanie będzie prawidłowe. Istnieje możliwość, że operacja cast kompiluje się prawidłowo, aby zakończyć się niepowodzeniem w czasie wykonywania. Jak pokazano w poniższym przykładzie, rzutowanie typu, które kończy się niepowodzeniem w czasie wykonywania, spowoduje wystąpienie <xref:System.InvalidCastException>.  
  
 [!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]  
  
 C#udostępnia operator [is](../../language-reference/operators/type-testing-and-cast.md#is-operator) , aby umożliwić przetestowanie pod kątem zgodności przed rzeczywistym przeprowadzeniem rzutowania. Aby uzyskać więcej informacji, zobacz [jak bezpiecznie rzutować przy użyciu dopasowania wzorca i operatorów AS i is](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).  
  
## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [konwersje](~/_csharplang/spec/conversions.md) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Typy](./index.md)
- [() — operator rzutowania](../../language-reference/operators/type-testing-and-cast.md#cast-operator-)
- [Zdefiniowane przez użytkownika operatory konwersji](../../language-reference/operators/user-defined-conversion-operators.md)
- [Konwersja uogólnionych typów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))
- [Instrukcje: konwertowanie ciągu na liczbę](./how-to-convert-a-string-to-a-number.md)
