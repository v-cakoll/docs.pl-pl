---
title: wielobieżność MDA
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, debugging
- transitioning threads unmanaged to managed code
- reentrancy MDA
- reentrancy without an orderly transition
- managed debugging assistants (MDAs), reentrancy
- illegal reentrancy
- MDAs (managed debugging assistants), reentrancy
- threading [.NET Framework], managed debugging assistants
- managed code, debugging
- native debugging, MDAs
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7de0a869925816da6df8f17e14ab92964aec8d11
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874188"
---
# <a name="reentrancy-mda"></a>wielobieżność MDA
`reentrancy` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy podejmowana jest próba przejścia z natywnego do zarządzanego kodu w przypadkach, gdzie wcześniejsze przełącznika z kodu zarządzanego do natywnego nie było wykonywane za pośrednictwem przejścia.  
  
## <a name="symptoms"></a>Symptomy  
 Sterty obiektów jest uszkodzony lub inne poważne błędy występują w przypadku przechodzenia z natywnego do zarządzanego kodu.  
  
 Wątki, przełączać się między kodu natywnego i zarządzanego w dowolnym kierunku, które należy wykonać przejścia. Jednak niektóre punkty rozszerzeń niskiego poziomu, w systemie operacyjnym, takich jak wektorowa obsługa wyjątków, umożliwia przełączników z kodu zarządzanego do natywnego kodu bez przeprowadzania przejścia.  Te przełączniki są pod kontrolą systemu operacyjnego, a nie kontrolowanymi języka wspólnego (CLR).  Kodu macierzystego, który jest wykonywany wewnątrz te punkty rozszerzeń należy unikać wywołań zwrotnych do kodu zarządzanego.  
  
## <a name="cause"></a>Przyczyna  
 Punkt rozszerzeń niskiego poziomu systemu operacyjnego, takie jak wektorowa obsługa wyjątków, zostało uaktywnione podczas wykonywania kodu zarządzanego.  Kod aplikacji, która jest wywoływana za pomocą tego punktu rozszerzalności podejmuje próbę wywołania zwrotnego w kodzie zarządzanym.  
  
 Ten problem, zawsze jest spowodowane przez kod aplikacji.  
  
## <a name="resolution"></a>Rozwiązanie  
 Sprawdź ślad stosu dla wątku, który uaktywnił to zdarzenie MDA.  Wątek podejmuje próbę nielegalnego mogą wywoływać kodu zarządzanego.  Ślad stosu powinno ujawnić, kod aplikacji przy użyciu tego punktu rozszerzalności, kod systemu operacyjnego, który zawiera ten punkt rozszerzeń i kodu zarządzanego, który został przerwany przez punkt rozszerzeń.  
  
 Na przykład zobaczysz MDA aktywacji w celu wywołania kodu zarządzanego z wewnątrz wektorowa obsługa wyjątków.  Na stosie zobaczysz obsługi kodu i niektórych kodu zarządzanego, takie jak wyzwolenie wyjątek wyjątków systemu operacyjnego <xref:System.DivideByZeroException> lub <xref:System.AccessViolationException>.  
  
 W tym przykładzie poprawnego rozpoznawania jest całkowicie zaimplementować wektorowa obsługa wyjątków w kodzie niezarządzanym.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA zgłasza, że niedozwolona wielobieżność zostanie podjęta.  Sprawdź stosu wątku w celu ustalenia, dlaczego to się dzieje i jak rozwiązać ten problem. Poniżej przedstawiono przykładowe dane wyjściowe.  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod powoduje, że przykład <xref:System.AccessViolationException> zostanie wygenerowany.  W wersjach systemu Windows, który obsługuje wektorowa wyjątków spowoduje to zarządzane wektorowa obsługa wyjątków do wywołania.  Jeśli `reentrancy` MDA jest włączona, MDA uaktywni się podczas próby wywołania `MyHandler` z systemu operacyjnego wyjątek wektorowa obsługi kod pomocy technicznej.  
  
```csharp
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter   
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,   
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,   
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)   
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()   
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try   
        {  
            // Dispatch on null should AV.  
            Reenter r = null;   
            r.Run();  
        }   
        catch { }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
