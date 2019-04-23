---
title: 'Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji'
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
ms.openlocfilehash: b39646655c175497533aa6dc358c6966acc27344
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325595"
---
# <a name="how-to-add-trace-statements-to-application-code"></a>Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji
Najczęściej używane do śledzenia przedstawiono metody do zapisywania danych wyjściowych odbiorniki: **Zapis**, **writeif —**, **WriteLine**, **WriteLineIf**, **Asercja**, i **się nie powieść**. Metody te można podzielić na dwie kategorie: **Zapis**, **WriteLine**, i **się nie powieść** wszystkie wyemituj dane wyjściowe bezwarunkowo, natomiast **writeif —**, **WriteLineIf**i  **Asercja** warunek logiczny, testowanie i go zapisuje lub nie zapisują na podstawie wartości warunku. **Writeif —** i **WriteLineIf** wyemituj dane wyjściowe, jeśli wynikiem warunku jest `true`, i **Asercja** emituje dane wyjściowe, jeśli warunek nie jest `false`.  
  
 Podczas projektowania usługi śledzenia i debugowania strategii, możesz pomyśleć o jak ma wyglądać dane wyjściowe. Wiele **zapisu** instrukcji wypełnione informacjami niepowiązanych spowoduje utworzenie dziennika, który jest trudny do odczytania. Z drugiej strony, przy użyciu **WriteLine** umieszczanie pokrewnych instrukcji w osobnych wierszach może utrudnić odróżnić, jakie informacje należy ze sobą. Ogólnie rzecz biorąc, używanych jest wiele **zapisu** instrukcji, jeśli chcesz połączyć informacje z wielu źródeł, aby utworzyć pojedynczy komunikat informacyjny i użyć **WriteLine** instrukcji, gdy chcesz utworzyć pojedynczy, pełny komunikat.  
  
### <a name="to-write-a-complete-line"></a>Aby zapisać pełny wiersz  
  
1. Wywołanie <xref:System.Diagnostics.Trace.WriteLine%2A> lub <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.  
  
     Znak powrotu karetki jest dołączany na końcu komunikat, ta metoda zwraca wartość, tak, aby następny komunikat zwrócony przez **zapisu**, **writeif —**, **WriteLine**, lub  **WriteLineIf —** rozpocznie się w następującym wierszu:  
  
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
  
### <a name="to-write-a-partial-line"></a>Aby zapisać wiersz częściowy  
  
1. Wywołanie <xref:System.Diagnostics.Trace.Write%2A> lub <xref:System.Diagnostics.Trace.WriteIf%2A> metody.  
  
     Następny komunikat przedmiotem **zapisu**, **writeif —**, **WriteLine**, lub **WriteLineIf** rozpocznie się w tym samym wierszu co komunikat przez **zapisu** lub **writeif —** instrukcji:  
  
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
  
1. Wywołaj <xref:System.Diagnostics.Trace.Assert%2A> metody.  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    >  Możesz użyć **Asercja** przy użyciu śledzenia i debugowania. W tym przykładzie generuje stos wywołań, aby wszelkie odbiornik **odbiorników** kolekcji. Aby uzyskać więcej informacji, zobacz [potwierdzenia w kodzie zarządzany](/visualstudio/debugger/assertions-in-managed-code) i <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Instrukcje: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [Przełączniki śledzenia](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [Obiekty nasłuchujące śledzenie](../../../docs/framework/debug-trace-profile/trace-listeners.md)
