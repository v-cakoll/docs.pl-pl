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
ms.openlocfilehash: 21df0e8129505e50e6b7f29c4f4f5aea94f380e3
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217466"
---
# <a name="how-to-add-trace-statements-to-application-code"></a>Porady: dodawanie instrukcji śledzenia do kodu aplikacji
Metody używane najczęściej do śledzenia to metody zapisywania danych wyjściowych dla odbiorników: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**i **niepowodzenia**. Te metody można podzielić na dwie kategorie: **zapis**, **WriteLine**i **Niepowodzenie** wszystkie dane wyjściowe Emituj bezwarunkowo, natomiast **WriteIf**, **WriteLineIf**i **Assert** testuje warunek logiczny, a następnie zapisują lub nie zapisu na podstawie wartości warunku. **WriteIf** i **WriteLineIf** Emituj dane wyjściowe, jeśli warunek jest `true`i **Assert** emituje dane wyjściowe, jeśli warunek jest `false`.  
  
 Podczas projektowania strategii śledzenia i debugowania należy zastanowić się, jak ma wyglądać dane wyjściowe. W przypadku wielu instrukcji **zapisu** zapełnione niepowiązane informacje spowodują utworzenie dziennika, który jest trudny do odczytania. Z drugiej strony, używanie funkcji **WriteLine** do umieszczania powiązanych instrukcji w osobnych wierszach może utrudnić odróżnienie informacji, jakie należą do siebie. Ogólnie rzecz biorąc, Użyj wielu instrukcji **Write** , jeśli chcesz połączyć informacje z wielu źródeł, aby utworzyć pojedynczy komunikat informacyjny, a następnie użyć instrukcji **WriteLine** , gdy chcesz utworzyć pojedynczy, kompletny komunikat.  
  
### <a name="to-write-a-complete-line"></a>Aby napisać kompletny wiersz  
  
1. Wywołanie <xref:System.Diagnostics.Trace.WriteLine%2A> lub <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.  
  
     Znak powrotu karetki jest dołączany na końcu wiadomości zwracanej przez tę metodę, dzięki czemu następny komunikat zwrócony przez **zapis**, **WriteIf**, **WriteLine**lub **WriteLineIf** rozpocznie się w następującym wierszu:  
  
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
  
### <a name="to-write-a-partial-line"></a>Aby napisać linię częściową  
  
1. Wywołanie <xref:System.Diagnostics.Trace.Write%2A> lub <xref:System.Diagnostics.Trace.WriteIf%2A> metody.  
  
     Następny komunikat umieszczony przez **zapis**, **WriteIf**, **WriteLine**lub **WriteLineIf** rozpocznie się w tym samym wierszu co komunikat umieszczony przez instrukcję **Write** lub **WriteIf** :  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a>Aby sprawdzić, czy określone warunki istnieją przed lub po wykonaniu metody  
  
1. Wywołaj metodę <xref:System.Diagnostics.Trace.Assert%2A>.  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > Można użyć metody **Assert** zarówno do śledzenia, jak i debugowania. Ten przykład wyprowadza stos wywołań do dowolnego odbiornika w kolekcji **odbiorników** . Aby uzyskać więcej informacji, zobacz [potwierdzenia w kodzie zarządzanym](/visualstudio/debugger/assertions-in-managed-code) i <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [Śledzenie i instrumentacja aplikacji](tracing-and-instrumenting-applications.md)
- [Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](how-to-create-initialize-and-configure-trace-switches.md)
- [Przełączniki śledzenia](trace-switches.md)
- [Obiekty nasłuchujące śledzenie](trace-listeners.md)
