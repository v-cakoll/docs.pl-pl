---
title: "Konwersja boxing i konwersja unboxing (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 893ef47c5e7522581b5d02489100942e47023a63
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Konwersja boxing i konwersja unboxing (Przewodnik programowania w języku C#)
Opakowanie jest proces konwersji [typu wartości](../../../csharp/language-reference/keywords/value-types.md) do typu `object` lub do dowolnego typu interfejsu zaimplementowany przez ten typ wartości. Gdy CLR pola typu wartości, opakowuje wartość wewnątrz elementu System.Object i zapisze go na stercie zarządzanej. Rozpakowywanie wyodrębnia typ wartości z obiektu. Opakowanie jest niejawne; Rozpakowywanie jest jawne. Pojęcie boxing i konwersja unboxing źródłową widoku unified C# system typów, w którym wartość dowolnego typu może być traktowana jako obiekt.  
  
 W poniższym przykładzie zmienna całkowitoliczbowa `i` jest *opakowany* i przypisany do obiektu `o`.  
  
 [!code-csharp[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]  
  
 Obiekt `o` może następnie być rozpakowany i przypisane zmienna całkowitoliczbowa `i`:  
  
 [!code-csharp[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]  
  
 Poniższe przykłady przedstawiają sposób opakowanie jest używana w języku C#.  
  
 [!code-csharp[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]  
  
## <a name="performance"></a>Wydajność  
 W odniesieniu do przypisania prostego opakowywanie i rozpakowywanie to procesy praktyce kosztowne. Gdy typ wartości jest opakowany, nowy obiekt musi przydzielone i zbudowane. W mniejszym stopniu rzutowanie wymagane dla Rozpakowywanie również jest kosztowne praktyce. Aby uzyskać więcej informacji, zobacz [wydajności](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).  
  
## <a name="boxing"></a>Boxing  
 Opakowanie jest używany do przechowywania typów wartości w stercie zbierane pamięci. Opakowanie jest niejawnej konwersji wartości [typu wartości](../../../csharp/language-reference/keywords/value-types.md) do typu `object` lub do dowolnego typu interfejsu zaimplementowany przez ten typ wartości. Konwersja boxing typów wartości przydziela wystąpienia obiektów na stercie i skopiowanie wartości do nowego obiektu.  
  
 Należy wziąć pod uwagę następujące deklaracja zmiennej typu wartość:  
  
 [!code-csharp[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]  
  
 Następująca instrukcja niejawnie stosuje operacja opakowanie w zmiennej `i`:  
  
 [!code-csharp[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]  
  
 Wynik tej instrukcji jest utworzenie odwołania do obiektu `o`, na stosie, który odwołuje się do wartości typu `int`, na stosie. Ta wartość jest kopią wartości typu wartość przypisaną do zmiennej `i`. Różnica między dwie zmienne `i` i `o`, przedstawiono na poniższej ilustracji.  
  
 ![BoxingConversion — grafika](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")  
Konwersja boxing  
  
 Istnieje również możliwość wykonania konwersji boxing jawnie jak w poniższym przykładzie, ale jawnej konwersji boxing nigdy nie jest wymagane:  
  
 [!code-csharp[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]  
  
## <a name="description"></a>Opis  
 W tym przykładzie konwertuje zmienna całkowitoliczbowa `i` do obiektu `o` za pomocą konwersji boxing. Następnie, wartość przechowywana w zmiennej `i` została zmieniona z `123` do `456`. W przykładzie pokazano, że oryginalny typ wartości obiektu spakowanego lokalizacjami osobną pamięć i dlatego mogą przechowywać różne wartości.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]  
  
## <a name="unboxing"></a>Rozpakowywanie  
 Rozpakowywanie jest jawna konwersja z typu `object` do [typu wartości](../../../csharp/language-reference/keywords/value-types.md) lub z typu interfejsu do typu wartości, który implementuje interfejs. Rozpakowywanie operacja obejmuje:  
  
-   Sprawdzanie, czy wystąpienie obiektu do upewnij się, że jest wartości spakowanej typu podanej wartości.  
  
-   Kopiowanie wartości z wystąpienia w zmiennej typu wartości.  
  
 Poniższe instrukcje pokazują zarówno konwersja boxing i rozpakowywanie operacje:  
  
 [!code-csharp[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]  
  
 Na poniższym rysunku pokazano wyniku poprzednich instrukcji.  
  
 ![Grafika konwersji Rozpakowującej](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")  
Konwersja unboxing  
  
 Dla Rozpakowywanie typów wartości się pomyślnie w czasie wykonywania element trwa rozpakowany musi być odwołaniem do obiektu, który został wcześniej utworzony przez konwersja boxing wystąpienia tego typu wartości. Podjęto próbę unbox — `null` powoduje, że <xref:System.NullReferenceException>. Podjęto próbę unbox — odwołanie do niezgodną wartość typu przyczyny <xref:System.InvalidCastException>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano przypadku nieprawidłowy Rozpakowywanie i powstałe w ten sposób `InvalidCastException`. Przy użyciu `try` i `catch`, gdy wystąpi błąd jest wyświetlany komunikat o błędzie.  
  
 [!code-csharp[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]  
  
 Ten program danych wyjściowych:  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 Jeśli zmienisz instrukcji:  
  
```  
int j = (short) o;  
```  
  
 na:  
  
```  
int j = (int) o;  
```  
  
 Konwersja zostanie wykonane, a otrzymasz dane wyjściowe:  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
-   [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
