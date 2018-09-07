---
title: Konwersja boxing i konwersja unboxing (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: ded8840231c4860d538eeb8c24d1472c60426087
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084832"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Konwersja boxing i konwersja unboxing (Przewodnik programowania w języku C#)
OPAKOWYWANIE to proces konwersji [typu wartości](../../../csharp/language-reference/keywords/value-types.md) typowi `object` lub dowolny typ interfejsu implementowany przez ten typ wartości. Gdy środowisko CLR opakowuje typ wartości, otacza wartość wewnątrz elementu System.Object i zapisuje go w zarządzanym stosie. Rozpakowywanie wyodrębnia typ wartości z obiektu. OPAKOWYWANIE jest niejawne; Rozpakowywanie jest jawne. Pojęcie pakowania i rozpakowywania źródłową C# postrzega system typów, w którym wartość dowolnego typu może być traktowana jako obiekt.  
  
 W poniższym przykładzie zmienna liczba całkowita `i` jest *opakowany* i przypisana do obiektu `o`.  
  
 [!code-csharp[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]  
  
 Obiekt `o` może następnie być rozpakowany i przypisany do zmiennej całkowitej `i`:  
  
 [!code-csharp[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]  
  
 Poniższe przykłady ilustrują, jak pakowanie jest używane w języku C#.  
  
 [!code-csharp[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]  
  
## <a name="performance"></a>Wydajność  
 Stosunku do prostych zadań pakowanie i rozpakowywanie są obciążającymi procesami. Gdy typ wartości jest zapakowany, nowy obiekt musi być przydzielane i zbudowane. W mniejszym stopniu cast wymagany do rozpakowywania również jest kosztowne praktyce. Aby uzyskać więcej informacji, zobacz [wydajności](../../../../docs/framework/performance/performance-tips.md).  
  
## <a name="boxing"></a>Boxing  
 OPAKOWYWANIE służy do przechowywania typów wartości w stosie zebranych elementów bezużytecznych. OPAKOWYWANIE to niejawna konwersja [typu wartości](../../../csharp/language-reference/keywords/value-types.md) typowi `object` lub dowolny typ interfejsu implementowany przez ten typ wartości. Opakowanie typu wartości przydziela wystąpienie obiektu do stosu i kopiuje wartość do nowego obiektu.  
  
 Rozważmy następującą deklarację zmiennej typu wartości:  
  
 [!code-csharp[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]  
  
 Poniższa instrukcja stosuje niejawnie operację pakowania na zmiennej `i`:  
  
 [!code-csharp[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]  
  
 Wyniku tego instrukcja tworzy odwołanie do obiektu `o`, na stosie, który odwołuje się do wartości typu `int`, na stosie. Ta wartość jest kopią wartości Typ-wartość przypisana do zmiennej `i`. Różnica między dwiema zmiennymi `i` i `o`, przedstawiono na poniższej ilustracji.  
  
 ![BoxingConversion — grafika](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")  
Konwersja boxing  
  
 Jest również możliwe przeprowadzenie pakowania, które jawnie jak w poniższym przykładzie, ale jawne pakowanie nigdy nie jest wymagane:  
  
 [!code-csharp[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]  
  
## <a name="description"></a>Opis  
 Ten przykład konwertuje zmienną całkowitą `i` do obiektu `o` za pomocą pakowania. Następnie wartość przechowywana w zmiennej `i` zostało zmienione z `123` do `456`. W przykładzie pokazano, że oryginalny typ wartości i spakowany obiekt Użyj lokalizacji pamięci i dlatego mogą przechowywać różne wartości.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]  
  
## <a name="unboxing"></a>Rozpakowywanie  
 Rozpakowywanie to konwersja jawna z typu `object` do [typu wartości](../../../csharp/language-reference/keywords/value-types.md) lub z typu interfejsu na typ wartości, która implementuje interfejs. Operacja rozpakowania składa się z:  
  
-   Sprawdzanie wystąpienie obiektu, aby upewnić się, że jest zapakowaną wartością danego typu wartości.  
  
-   Kopiowanie wartości z instancji do zmiennej typu wartości.  
  
 Następujące instrukcje pokazują zarówno pakowania, jak i rozpakowania operacje:  
  
 [!code-csharp[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]  
  
 Następujący rysunek ilustruje wynik poprzednich instrukcji.  
  
 ![Grafika przedstawiająca konwersję unBoxing](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")  
Konwersja rozpakowująca  
  
 Dla rozpakowywania typów wartości, które zakończyło się sukcesem w czasie wykonywania, rozpakowywany element musi być odwołaniem do obiektu, który został wcześniej utworzony przez pakowanie instancji tego typu wartości. Próba rozpakowania `null` powoduje, że <xref:System.NullReferenceException>. Próba rozpakowania odwołania do niezgodną wartość typu powoduje, że <xref:System.InvalidCastException>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje przypadek nieprawidłowy Rozpakowywanie i wynikowy `InvalidCastException`. Za pomocą `try` i `catch`, komunikat o błędzie jest wyświetlany, gdy wystąpi błąd.  
  
 [!code-csharp[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]  
  
 Ten program wyświetla:  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 Jeśli zmienisz instrukcję:  
  
```csharp
int j = (short) o;  
```  
  
 na:  
  
```csharp
int j = (int) o;  
```  
  
 Konwersja zostanie przeprowadzona i otrzymasz dane wyjściowe:  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
-   [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
