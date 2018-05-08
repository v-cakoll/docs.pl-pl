---
title: Rzutowanie i konwersje typów (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 0c17fc89d93bdbb01bdef7935e72f8a7d96b0a55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="casting-and-type-conversions-c-programming-guide"></a>Rzutowanie i konwersje typów (Przewodnik programowania w języku C#)
C# jest wpisany statycznie w czasie kompilacji, po zadeklarowaniu zmiennej, nie można ponownie zadeklarować lub używany do przechowywania wartości innego typu, o ile nie jest możliwe do przekonwertowania na typ zmiennej typu. Na przykład nie jest konwersja z typu integer do dowolnego ciągu dowolnych. W związku z tym po deklaracji `i` jako liczba całkowita, nie można przypisać ciąg "Hello", jak to pokazano w poniższym kodzie.  
  
```csharp  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 Jednak czasami może być konieczne skopiuj wartość do zmiennej lub metody parametr innego typu. Na przykład może być zmienną liczbą całkowitą, który należy przekazać do metody, których parametr jest typu `double`. Można też przypisać zmiennej klasy do zmiennej typu interfejsu. Tego rodzaju działania są nazywane *konwersje typów*. W języku C# można wykonywać następujące rodzaje konwersji:  
  
-   **Niejawne konwersje**: żadna specjalna składnia jest wymagana, ponieważ konwersja jest typu bezpieczne i żadne dane nie zostaną utracone. Przykładami konwersje z mniejszym do większych typów całkowitych i konwersje z klas pochodnych do klasy podstawowej.  
  
-   **Jawne konwersje (rzutowania)**: jawne konwersje wymaga operatora rzutowania. Rzutowanie jest wymagany, gdy informacje mogą zostać utracone podczas konwersji, lub gdy Konwersja może się nie powieść z innych powodów.  Typowe przykłady numerycznej konwersji do typu, który ma mniej precyzję lub mniejszego zakresu, a także konwersji wystąpienia klasy podstawowej do klasy pochodnej.  
  
-   **Konwersje zdefiniowane przez użytkownika**: konwersje zdefiniowane przez użytkownika są wykonywane przez specjalne metody definiujące umożliwia jawne i niejawne konwersje między niestandardowych typów, które nie mają relacji — Klasa pochodna klasy podstawowej. Aby uzyskać więcej informacji, zobacz [operatory konwersji](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).  
  
-   **Konwersje z klasy pomocy**: umożliwia konwersję pomiędzy niezgodnych typów, takich jak liczby całkowite i <xref:System.DateTime?displayProperty=nameWithType> obiektów, lub ciągów szesnastkowych i tablice typu byte, można użyć <xref:System.BitConverter?displayProperty=nameWithType> klasy <xref:System.Convert?displayProperty=nameWithType> klasy i `Parse`typy metod wbudowanych liczbowe, takie jak <xref:System.Int32.Parse%2A?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [porady: Konwertowanie tablicy typu byte na liczbę całkowitą](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [porady: konwertowanie ciągu na liczbę](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), i [jak: konwertowanie między ciągów szesnastkowych i typy liczbowe](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).  
  
## <a name="implicit-conversions"></a>Niejawne konwersje  
 Dla typów numerycznych wbudowanych niejawna konwersja można wprowadzić, gdy wartości do przechowywania można umieścić w zmiennej, bez jest obcięty lub zaokrąglony. Na przykład zmienna typu [długi](../../../csharp/language-reference/keywords/long.md) (liczba całkowita 8 bajtów) może przechowywać wszystkie wartości [int](../../../csharp/language-reference/keywords/int.md) (4 bajty na komputerze 32-bitowym) może przechowywać. W poniższym przykładzie, kompilator niejawnie konwertuje wartość prawej strony na typ `long` przed przypisaniem go do `bigNum`.  
  
 [!code-csharp[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 Aby uzyskać pełną listę wszystkich niejawne konwersje liczbowe, zobacz [niejawne numeryczne Tabela konwersji](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Dla typów referencyjnych zawsze niejawna konwersja istnieje z klasy do jednego z jego bezpośredniej lub pośredniej klasy podstawowej lub do interfejsów. Żadna specjalna składnia jest konieczne, ponieważ klasa pochodna zawsze zawiera wszystkie elementy członkowskie klasy podstawowej.  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>Jawne konwersje  
 Jednak jeśli konwersji nie mogą być nawiązywane bez ryzyka utraty informacji, kompilator wymaga wykonania jawnej konwersji, która jest wywoływana *rzutowania*. Rzutowanie jest sposób jawnie informowania kompilatora, którego zamierzasz dokonać konwersji i że masz świadomość, że może dojść do utraty danych. Aby wykonać rzutowanie, określ typ, które są rzutowania w nawiasach wartość lub zmienna ma zostać przekonwertowany. Następujące program rzutowania [podwójne](../../../csharp/language-reference/keywords/double.md) do [int](../../../csharp/language-reference/keywords/int.md). Program nie zostanie skompilowany bez rzutowania.  
  
 [!code-csharp[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 Lista jawnych konwersji liczbowych, które są dozwolone, zobacz [jawne numeryczne Tabela konwersji](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
 Dla typu odwołania jawnego rzutowania jest wymagany, jeśli chcesz konwertować z typu podstawowego na pochodny typ:  
  
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
  
 Operacji rzutowania między typy referencyjne nie zmienia typu czasu wykonywania obiektu podstawowego; zmienia tylko typ wartości, który jest używany jako odwołanie do tego obiektu. Aby uzyskać więcej informacji, zobacz [polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="type-conversion-exceptions-at-run-time"></a>Typ konwersji wyjątków w czasie wykonywania  
 W niektórych konwersje typu odwołania kompilator nie może określić, czy rzutowanie będzie nieprawidłowa. Istnieje możliwość dla operacji rzutowania kompilowany poprawnie się niepowodzeniem w czasie wykonywania. Jak pokazano w poniższym przykładzie, typu rzutowania spowoduje kończy się niepowodzeniem w czasie wykonywania <xref:System.InvalidCastException> zostanie wygenerowany.  
  
 [!code-csharp[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 C# zawiera [jest](../../../csharp/language-reference/keywords/is.md) i [jako](../../../csharp/language-reference/keywords/as.md) operatory umożliwiają do testowania zgodności przed rzeczywistego wykonania rzutowanie. Aby uzyskać więcej informacji, zobacz [porady: bezpieczne rzutowanie za pomocą, jak i jest operatory](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [(), operator](../../../csharp/language-reference/operators/invocation-operator.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)  
 [implicit](../../../csharp/language-reference/keywords/implicit.md)  
 [Operatory konwersji](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [Konwersja typów ogólnych](http://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada)  
 [Konwersja wyeksportowanego typu](http://msdn.microsoft.com/library/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)  
 [Instrukcje: konwertowanie ciągu na liczbę](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
