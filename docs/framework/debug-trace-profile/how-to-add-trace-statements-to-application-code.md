---
title: 'Porady: dodawanie instrukcji śledzenia do kodu aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ed85c73182da5d911c6cc84fba26c658412ac158
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391371"
---
# <a name="how-to-add-trace-statements-to-application-code"></a>Porady: dodawanie instrukcji śledzenia do kodu aplikacji
Najczęściej używane do śledzenia przedstawiono metody do zapisywania danych wyjściowych do odbiorników: **zapisu**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, i **niepowodzenie**. Te metody można podzielić na dwie kategorie: **zapisu**, **WriteLine**, i **niepowodzenie** wszystkie Emituj danych wyjściowych bezwarunkowo, podczas gdy **WriteIf**, **WriteLineIf**, i **Assert** przetestować warunek typu Boolean i zapisu lub nie zapisuj oparte na wartości warunku. **WriteIf** i **WriteLineIf** Emituj danych wyjściowych, jeśli wynikiem warunku jest `true`, i **Assert** emituje dane wyjściowe, jeśli wynikiem warunku jest `false`.  
  
 Podczas projektowania sieci śledzenie i debugowanie strategii, możesz pomyśleć o sposób dane wyjściowe do wyszukiwania. Wiele **zapisu** instrukcje wypełniane informacjami niepowiązanych utworzy dziennika, który jest trudny do odczytania. Z drugiej strony, przy użyciu **WriteLine** umieszczanie pokrewne instrukcje w osobnych wierszach może utrudniać rozróżnienie, jakie informacje należy razem. Ogólnie rzecz biorąc, używając wielu **zapisu** instrukcji, gdy chcesz połączyć informacje z wielu źródeł, aby utworzyć jeden komunikat informacyjny i użyj **WriteLine** instrukcji, gdy chcesz utworzyć pełną, jeden komunikat.  
  
### <a name="to-write-a-complete-line"></a>Aby zapisać pełny wiersz  
  
1.  Wywołanie <xref:System.Diagnostics.Trace.WriteLine%2A> lub <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.  
  
     Znak powrotu karetki jest dołączany na końcu ta metoda zwraca komunikat tak, aby następny komunikat zwrócony przez **zapisu**, **WriteIf**, **WriteLine**, lub  **WriteLineIf** rozpocznie się o następujący wiersz:  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,   
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a>Do zapisywania częściowej wiersza  
  
1.  Wywołanie <xref:System.Diagnostics.Trace.Write%2A> lub <xref:System.Diagnostics.Trace.WriteIf%2A> metody.  
  
     Następny komunikat przedmiotem **zapisu**, **WriteIf**, **WriteLine**, lub **WriteLineIf** rozpocznie się na tym samym wierszu co komunikat przez **zapisu** lub **WriteIf** instrukcji:  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,   
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a>Aby sprawdzić, że niektóre warunki przed lub po wykonaniu metody  
  
1.  Wywołanie <xref:System.Diagnostics.Trace.Assert%2A> metody.  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    >  Można użyć **Assert** śledzenia i debugowania. Stos wywołań żadnych odbiornika w danych wyjściowych w tym przykładzie **odbiorników** kolekcji. Aby uzyskać więcej informacji, zobacz [potwierdzenia w kod zarządzany](/visualstudio/debugger/assertions-in-managed-code) i <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>  
 [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [Przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [Obiekty nasłuchujące śledzenie](../../../docs/framework/debug-trace-profile/trace-listeners.md)
