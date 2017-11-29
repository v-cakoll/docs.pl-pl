---
title: "Porady: łączenie wielu ciągów (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca240523e2483289e11433fd58d9630a31721b33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a>Porady: łączenie wielu ciągów (Przewodnik programowania w języku C#)
*Łączenie* to proces dołączania jeden ciąg do końca ciągu innego. Jeśli łączenie literałów ciągu lub ciągu stałych przy użyciu `+` operatora, kompilator tworzy pojedynczy ciąg. Nie można uruchomić wystąpieniu łączenia. Jednak zmiennych ciągu może zostać dołączona tylko w czasie wykonywania. W takim przypadku zapoznaj się z różnych metod jego wpływu na wydajność.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak podzielić ciąg literału na mniejsze ciągów w celu zwiększenia czytelności w kodzie źródłowym. Te elementy zostaną połączone w jeden ciąg w czasie kompilacji. Nie jest uruchamiane koszt niezależnie od liczby ciągów związanych wydajności w czasie.  
  
 [!code-csharp[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## <a name="example"></a>Przykład  
 Aby połączyć zmiennych ciągu można użyć `+` lub `+=` operatorów, lub <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody. `+` Operator jest łatwy w użyciu i sprawia, że dla intuicyjne kodu. Nawet jeśli używasz kilka + operatory w jednej instrukcji, ciąg zawartości jest kopiowany tylko raz. Ale jeśli Powtórz tę operację wiele razy na przykład w pętli, może powodować problemy wydajności. Na przykład należy uwzględnić następujący kod:  
  
 [!code-csharp[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  W operacji łączenia ciąg kompilatora C# traktuje pusty ciąg takie same jak pusty ciąg, ale nie konwertuje wartość oryginalnego pusty ciąg.  
  
 Jeśli nie są łączenie wielu ciągów (na przykład w pętli), to koszt wydajności ten kod prawdopodobnie nie ma znaczenia. Dotyczy to także <xref:System.String.Concat%2A?displayProperty=nameWithType> i <xref:System.String.Format%2A?displayProperty=nameWithType> metody.  
  
 Jednak gdy wydajności odgrywa ważną rolę, należy zawsze używać <xref:System.Text.StringBuilder> klasy do ciągów. Poniższy kod używa <xref:System.Text.StringBuilder.Append%2A> metody <xref:System.Text.StringBuilder> klasy do ciągów bez wpływu CBC `+` operatora.  
  
 [!code-csharp[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Ciągi](../../../csharp/programming-guide/strings/index.md)
