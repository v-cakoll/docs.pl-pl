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
ms.openlocfilehash: 5cbe8e843ad72785010240f3db30b1d344c80650
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181763"
---
# <a name="reentrancy-mda"></a>wielobieżność MDA
Asystent `reentrancy` debugowania zarządzanego (MDA) jest aktywowany, gdy podejmowana jest próba przejścia z kodu macierzystego do zarządzanego w przypadkach, gdy wcześniejsze przejście z kodu natywnego nie zostało wykonane za pośrednictwem uporządkowanego przejścia.  
  
## <a name="symptoms"></a>Objawy  
 Sterta obiektu jest uszkodzona lub inne poważne błędy występują podczas przechodzenia z kodu macierzystego do zarządzanego.  
  
 Wątki, które przełączają się między kodem macierzystym i zarządzanym w obu kierunkach, muszą wykonać uporządkowane przejście. Jednak niektóre punkty rozszerzalności niskiego poziomu w systemie operacyjnym, takie jak program obsługi wyjątków wektorowych, umożliwiają przełączanie z kodu natywnego bez przeprowadzania uporządkowanego przejścia.  Te przełączniki są pod kontrolą systemu operacyjnego, a nie pod kontrolą wspólnego środowiska wykonawczego języka (CLR).  Każdy kod macierzysty, który wykonuje wewnątrz tych punktów rozszerzalności należy unikać wywoływania z powrotem do kodu zarządzanego.  
  
## <a name="cause"></a>Przyczyna  
 Niski poziom punktu rozszerzalności systemu operacyjnego, takich jak wektorowy program obsługi wyjątków, został aktywowany podczas wykonywania kodu zarządzanego.  Kod aplikacji, który jest wywoływany za pośrednictwem tego punktu rozszerzalności próbuje wywołać z powrotem do kodu zarządzanego.  
  
 Ten problem jest zawsze spowodowany przez kod aplikacji.  
  
## <a name="resolution"></a>Rozwiązanie  
 Sprawdź ślad stosu dla wątku, który aktywował ten MDA.  Wątek próbuje nielegalnie wywołać kod zarządzany.  Ślad stosu powinien ujawnić kod aplikacji przy użyciu tego punktu rozszerzalności, kod systemu operacyjnego, który zapewnia ten punkt rozszerzalności i kod zarządzany, który został przerwany przez punkt rozszerzalności.  
  
 Na przykład zostanie wyświetlony MDA aktywowany w próbie wywołania kodu zarządzanego z wewnątrz wektorowego programu obsługi wyjątków.  Na stosie zobaczysz kod obsługi wyjątków systemu operacyjnego i niektóre <xref:System.DivideByZeroException> kody <xref:System.AccessViolationException>zarządzane wyzwalające wyjątek, taki jak a lub .  
  
 W tym przykładzie prawidłowe rozwiązanie jest do zaimplementowania wektorowego obsługi wyjątków całkowicie w kodzie niezarządzanym.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na czas działania  
 To MDA nie ma wpływu na CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA informuje, że podejmowane są próby nielegalnego ponownego wejścia na boja.  Sprawdź stos wątku, aby ustalić, dlaczego tak się dzieje i jak rozwiązać problem. Poniżej przedstawiono dane wyjściowe próbki.  
  
```output
Additional Information: Attempting to call into managed code without
transitioning out first.  Do not attempt to run managed code inside
low-level native extensibility points. Managed Debugging Assistant
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a>Konfigurowanie  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu <xref:System.AccessViolationException> powoduje, że mają być generowane.  W wersjach systemu Windows, które obsługują wektorowe obsługi wyjątków, spowoduje to, że zarządzany program obsługi wyjątków wektorowych do wywołania.  Jeśli `reentrancy` MDA jest włączona, MDA aktywuje się `MyHandler` podczas próby wywołania z systemu operacyjnego wektorowe kod obsługi wyjątków.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
