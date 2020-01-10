---
title: Pakowanie i rozpakowywanie — C# Przewodnik programistyczny
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 4c17ba1917589dfd534b53ee3fb3efe67ddd02d7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698797"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Konwersja boxing i konwersja unboxing (Przewodnik programowania w języku C#)
Opakowanie to proces konwersji [typu wartości](../../language-reference/keywords/value-types.md) na typ `object` lub na dowolny typ interfejsu implementowany przez ten typ wartości. Gdy środowisko CLR pola typu wartości, zawija wartość wewnątrz wystąpienia <xref:System.Object?displayProperty=nameWithType> i zapisuje je na stosie zarządzanym. Rozpakowywanie wyodrębnia typ wartości z obiektu. Opakowanie jest niejawne; Rozpakowywanie jest jawne. Pojęcie opakowania i rozpakowywanie opiera się na C# ujednoliconym widoku systemu typów, w którym wartość dowolnego typu może być traktowana jako obiekt.  
  
 W poniższym przykładzie zmienna Integer `i` jest *opakowana* i przypisana do `o`obiektu.  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 Obiekt `o` może być następnie rozpakowany i przypisany do zmiennej całkowitej `i`:  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 W poniższych przykładach pokazano, jak opakowanie jest używane C#w programie.  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a>Wydajność  
 W odniesieniu do prostych przydziałów, opakowanie i rozpakowywanie są w sposób obliczeniowy kosztowny. Gdy typ wartości jest opakowany, nowy obiekt musi być przydzielony i skonstruowany. W mniejszym stopniu rzutowanie wymagane do rozpakowywania jest również kosztowne w praktyce. Aby uzyskać więcej informacji, zobacz [wydajność](../../../framework/performance/performance-tips.md).  
  
## <a name="boxing"></a>Boxing  
 Opakowanie jest używane do przechowywania typów wartości w stosie zebranych elementów bezużytecznych. Opakowanie jest niejawną konwersją [typu wartości](../../language-reference/keywords/value-types.md) na typ `object` lub do dowolnego typu interfejsu zaimplementowanego przez ten typ wartości. Opakowanie typu wartości przydziela wystąpienie obiektu na stercie i kopiuje wartość do nowego obiektu.  
  
 Rozważmy następującą deklarację zmiennej typu wartości:  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 Poniższa instrukcja niejawnie stosuje operację pakowania na zmiennej `i`:  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 Wynikiem tej instrukcji jest utworzenie odwołania do obiektu `o`na stosie, który odwołuje się do wartości typu `int`, na stercie. Ta wartość jest kopią wartości typu wartości przypisanej do zmiennej `i`. Różnica między dwoma zmiennymi, `i` i `o`, przedstawiono na poniższej ilustracji konwersji pakującej:  
  
 ![Ilustracja przedstawiająca różnicę między zmiennymi i i o.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)    
  
 Istnieje również możliwość, że opakowanie zostało jawnie wykonane, jak w poniższym przykładzie, ale jawne opakowanie nigdy nie jest wymagane:  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a>Opis  
 Ten przykład konwertuje zmienną typu Integer `i` do obiektu `o` przy użyciu opakowania. Następnie wartość przechowywana w zmiennej `i` jest zmieniana z `123` na `456`. W przykładzie pokazano, że oryginalny typ wartości i obiekt opakowany używają oddzielnych lokalizacji pamięci, w związku z czym można przechowywać różne wartości.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]  
  
## <a name="unboxing"></a>Rozpakowywanie  
 Rozpakowywanie jest jawną konwersją z typu `object` do [typu wartości](../../language-reference/keywords/value-types.md) lub z typu interfejsu na typ wartości implementującej interfejs. Odpakowywanie operacji składa się z:  
  
- Sprawdzanie wystąpienia obiektu, aby upewnić się, że jest to opakowana wartość danego typu wartości.  
  
- Kopiowanie wartości z wystąpienia do zmiennej typu wartości.  
  
 Następujące instrukcje przedstawiają operacje pakowania i rozpakowywania:  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 Na poniższej ilustracji przedstawiono wynik poprzednich instrukcji: 
  
 ![Ilustracja przedstawiająca konwersję rozpakowywanie.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)
  
 Aby rozpakowywanie typów wartości zakończyło się pomyślnie w czasie wykonywania, element, który jest rozpakowany, musi być odwołaniem do obiektu, który został wcześniej utworzony przez opakowanie wystąpienia tego typu wartości. Próba Unbox `null` powoduje <xref:System.NullReferenceException>. Próba Unbox odwołania do niezgodnego typu wartości powoduje wystąpienie <xref:System.InvalidCastException>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje przypadek nieprawidłowego rozpakowywania i powstające `InvalidCastException`. Przy użyciu `try` i `catch`, zostanie wyświetlony komunikat o błędzie po wystąpieniu błędu.  
  
 [!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]  
  
 Ten program wyprowadza:  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 W przypadku zmiany instrukcji:  
  
```csharp
int j = (short) o;  
```  
  
 na:  
  
```csharp
int j = (int) o;  
```  
  
 Konwersja zostanie wykonana i otrzymasz dane wyjściowe:  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
- [Typy odwołań](../../language-reference/keywords/reference-types.md)  
  
- [Typy wartości](../../language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
