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
ms.openlocfilehash: 5aea903a7b16491a84998d8290270044e167b79f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="reentrancy-mda"></a>wielobieżność MDA
`reentrancy` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy podejmowana jest próba przejście z kodu natywnego do zarządzanego kodu w przypadkach, gdy wcześniejsze przełącznika z kodu zarządzanego do natywnego nie została wykonana za pomocą uporządkowanego przejścia.  
  
## <a name="symptoms"></a>Symptomy  
 Sterty obiektów jest uszkodzony lub innych błędów występujących podczas przejścia z kodu natywnego do zarządzanego kodu.  
  
 Wątki przełączania się między kodu natywnego i zarządzanego w żadnym kierunku, należy wykonać uporządkowanego przejścia. Jednak niektórych punktów rozszerzalności niskiego poziomu systemu operacyjnego, takich jak wektorowa obsługa wyjątków, Zezwalaj przełączników z zarządzanego do kodu macierzystego bez uporządkowanego przejścia.  Te przełączniki są pod kontrolą systemu operacyjnego, a nie pod kontrolą języka wspólnego (CLR).  Kod natywny, wykonujący wewnątrz tych punktów rozszerzalności należy unikać wywołań zwrotnych do kodu zarządzanego.  
  
## <a name="cause"></a>Przyczyna  
 Punktów rozszerzalności niskiego poziomu systemu operacyjnego, takich jak wektorowa obsługa wyjątków, zostało uaktywnione podczas wykonywania kodu zarządzanego.  Kod aplikacji, które jest wywoływane przez ten punkt rozszerzalności próbuje wywołanie zwrotne do kodu zarządzanego.  
  
 Przyczyną tego problemu jest zawsze kodu aplikacji.  
  
## <a name="resolution"></a>Rozwiązanie  
 Sprawdź, czy śledzenia stosu dla wątku, który został aktywowany to zdarzenie MDA.  Wątek próbuje nielegalnego wywołania wewnątrz kodu zarządzanego.  Ślad stosu powinno ujawnić kod aplikacji przy użyciu tego punktu rozszerzalności, kod systemu operacyjnego, który zawiera ten punkt rozszerzeń i kod zarządzany, który został przerwany przez punkt rozszerzeń.  
  
 Na przykład zobaczysz MDA aktywować próba wywołania kodu zarządzanego z wewnątrz wektorowa obsługa wyjątków.  Na stosie zobaczysz obsługi kodu i niektóre kod zarządzany, takich jak wyzwalają wyjątek wyjątków systemu operacyjnego <xref:System.DivideByZeroException> lub <xref:System.AccessViolationException>.  
  
 W tym przykładzie poprawnego rozpoznawania jest całkowicie implementacja wektorowa obsługa wyjątków za pomocą kodu niezarządzanego.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA zgłasza, że niedozwolona wielobieżność podjęto próbę.  Sprawdź, czy stosu wątku w celu ustalenia, dlaczego zdarza się to i sposobu rozwiązania problemu. Oto przykładowe dane wyjściowe.  
  
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
 Poniższy kod przyczyny przykład <xref:System.AccessViolationException> zostanie wygenerowany.  W wersjach systemu Windows, który obsługi wyjątków wektorowa spowoduje to zarządzany wektorowa obsługa wyjątków do wywołania.  Jeśli `reentrancy` MDA jest włączona, MDA uaktywni się podczas próby wywołania `MyHandler` z systemu operacyjnego wyjątek wektorowa obsługa kodu pomocy technicznej.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
