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
ms.openlocfilehash: 9903a0357d1d8ceade21b590fd54c8cab517f134
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174748"
---
# <a name="how-to-add-trace-statements-to-application-code"></a>Porady: dodawanie instrukcji śledzenia do kodu aplikacji
Metody stosowane najczęściej do śledzenia są metody pisania danych wyjściowych do odbiorników: **Write**, **WriteIf**, **WriteLine**, WriteLine , **WriteLine ,** **Assert**, i **Fail**. Metody te można podzielić na dwie kategorie: **Write**, Write , **WriteLine**i **Fail** wszystkie emitują dane wyjściowe bezwarunkowo, natomiast **WriteIf**, **WriteLineIf**i **Assert** testować warunek logiczny i zapisywać lub nie zapisywać na podstawie wartości warunku. **WriteIf** i **WriteLineIf** emitują `true`dane wyjściowe, jeśli warunek `false`jest , i **Assert** emituje dane wyjściowe, jeśli warunek jest .  
  
 Podczas projektowania strategii śledzenia i debugowania, należy pomyśleć o tym, jak mają wyglądać dane wyjściowe. Wiele **instrukcji Write** wypełnione niepowiązanych informacji utworzy dziennik, który jest trudny do odczytania. Z drugiej strony za pomocą **WriteLine** umieścić powiązane instrukcje w oddzielnych wierszach może utrudnić rozróżnienie, jakie informacje należą do siebie. Ogólnie rzecz biorąc, należy użyć wielu **Write** instrukcji, gdy chcesz połączyć informacje z wielu źródeł, aby utworzyć jedną wiadomość informacyjną i użyj **WriteLine** instrukcji, gdy chcesz utworzyć pojedynczą, pełną wiadomość.  
  
### <a name="to-write-a-complete-line"></a>Aby napisać pełny wiersz  
  
1. Wywołanie <xref:System.Diagnostics.Trace.WriteLine%2A> lub <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.  
  
     Powrót karetki jest dołączany na końcu wiadomości zwraca tej metody, tak aby następna wiadomość zwrócona przez **Write**, **WriteIf**, **WriteLine**lub **WriteLineIf** rozpocznie się w następującym wierszu:  
  
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
  
### <a name="to-write-a-partial-line"></a>Aby napisać wiersz częściowy  
  
1. Wywołanie <xref:System.Diagnostics.Trace.Write%2A> lub <xref:System.Diagnostics.Trace.WriteIf%2A> metody.  
  
     Następna wiadomość wystawiona przez **Write**, **WriteIf**, **WriteLine**lub **WriteLineIf** rozpocznie się w tym samym wierszu, co wiadomość wystawiona przez **Write** lub **WriteIf** instrukcji:  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a>Aby sprawdzić, czy istnieją określone warunki przed lub po wykonaniu metody  
  
1. Wywołanie <xref:System.Diagnostics.Trace.Assert%2A> metody.  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > Można użyć **Assert** zarówno śledzenia i debugowania. W tym przykładzie wyprowadza stos wywołań do dowolnego odbiornika w **kolekcji odbiorników.** Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>potwierdzenia w [kodzie zarządzanym](/visualstudio/debugger/assertions-in-managed-code) i .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [Śledzenie i instrumentacja aplikacji](tracing-and-instrumenting-applications.md)
- [Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia](how-to-create-initialize-and-configure-trace-switches.md)
- [Przełączniki śledzenia](trace-switches.md)
- [Obiekty nasłuchujące śledzenia](trace-listeners.md)
