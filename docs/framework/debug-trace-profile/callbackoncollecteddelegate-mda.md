---
title: callbackOnCollectedDelegate MDA
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- managed debugging assistants (MDAs), callback on collected delegates
- MDAs (managed debugging assistants), callback on collected delegates
- callback on delegate after garbage collection
- callbackOnCollectedDelegate MDA
- managed debugging assistants (MDAs), garbage collection
- call back collected delegates
- garbage collection, run-time errors
- delegates [.NET Framework], garbage collection
ms.assetid: 398b0ce0-5cc9-4518-978d-b8263aa21e5b
ms.openlocfilehash: d4ca777fa5b41433eec227762fe315f22ab33cf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174228"
---
# <a name="callbackoncollecteddelegate-mda"></a>callbackOnCollectedDelegate MDA
Zarządzany `callbackOnCollectedDelegate` asystent debugowania (MDA) jest aktywowany, jeśli pełnomocnik jest organizowany z zarządzanego kodu jako wskaźnik funkcji i wywołania zwrotnego jest umieszczana na tym wskaźniku funkcji po delegat został zebranych śmieci.  
  
## <a name="symptoms"></a>Objawy  
 Naruszenia dostępu występują podczas próby wywołania kodu zarządzanego za pomocą wskaźników funkcji, które zostały uzyskane od zarządzanych delegatów. Te błędy, podczas gdy nie ma błędów wspólnego środowiska wykonawczego języka (CLR), może wydawać się tak, ponieważ naruszenie zasad dostępu występuje w kodzie CLR.  
  
 Błąd nie jest spójny; czasami wywołanie wskaźnika funkcji powiedzie się, a czasami kończy się niepowodzeniem. Awaria może wystąpić tylko przy dużym obciążeniu lub przy losowej liczbie prób.  
  
## <a name="cause"></a>Przyczyna  
 Delegat, z którego został utworzony wskaźnik funkcji i narażone na kod niezarządzane został zebranych śmieci. Gdy składnik niezarządzane próbuje wywołać wskaźnik funkcji, generuje naruszenie zasad dostępu.  
  
 Błąd pojawia się losowo, ponieważ zależy od tego, kiedy występuje wyrzucanie elementów bezużytecznych. Jeśli pełnomocnik kwalifikuje się do odbioru, wyrzucania elementów bezużytecznych może wystąpić po wywołaniu zwrotnym i wywołanie zakończy się pomyślnie. W innych przypadkach wyrzucania elementów bezużytecznych występuje przed wywołaniem zwrotnym, wywołanie zwrotne generuje naruszenie zasad dostępu, a program zatrzymuje.  
  
 Prawdopodobieństwo awarii zależy od czasu między kierowanie delegata i wywołania zwrotnego na wskaźnik funkcji, a także częstotliwość wyrzucania elementów bezużytecznych. Błąd jest sporadyczne, jeśli czas między kierowanie delegata i wywołanie zwrotne wynika jest krótki. Zazwyczaj jest tak, jeśli metoda niezarządzana odbierająca wskaźnik funkcji nie zapisuje wskaźnika funkcji do późniejszego użycia, ale zamiast tego natychmiast wywołuje wskaźnik funkcji, aby zakończyć jego działanie przed zwróceniem. Podobnie więcej wyrzucania elementów bezużytecznych występuje, gdy system jest pod dużym obciążeniem, co sprawia, że bardziej prawdopodobne, że wyrzucanie elementów bezużytecznych wystąpi przed wywołaniem zwrotnym.  
  
## <a name="resolution"></a>Rozwiązanie  
 Gdy delegat został zorganizowany jako wskaźnik funkcji niezarządzane, moduł zbierający elementy bezużyteczne nie może śledzić jego istnienia. Zamiast tego kod musi zachować odwołanie do pełnomocnika przez cały okres istnienia wskaźnika funkcji niezarządzanej. Ale zanim będzie można to zrobić, należy najpierw określić, który delegat został zebrany. Po aktywowaniu mda, zawiera nazwę typu delegata. Ta nazwa służy do wyszukiwania kodu dla platformy wywołać lub sygnatury COM, które przekazują, że delegata do kodu niezarządzanego. Pełnomocnik naruszający jest przekazywane za pośrednictwem jednej z tych witryn wywołania. Można również włączyć `gcUnmanagedToManaged` MDA wymusić wyrzucania elementów bezużytecznych przed każdym wywołania zwrotnego w czasie wykonywania. Spowoduje to usunięcie niepewności wprowadzone przez wyrzucania elementów bezużytecznych, zapewniając, że wyrzucanie elementów bezużytecznych zawsze występuje przed wywołaniem zwrotnym. Gdy wiesz, co delegat został zebrany, należy zmienić kod, aby zachować odwołanie do tego delegata po stronie zarządzanej przez cały okres istnienia wskaźnika funkcji niezarządzanej.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na czas działania  
 Gdy delegaci są organizowane jako wskaźniki funkcji, środowisko wykonawcze przydziela thunk, który wykonuje przejście z niezarządzane do zarządzanego. To thunk jest to, co kod niezarządzany faktycznie wywołuje przed zarządzanym delegatem jest ostatecznie wywoływane. Bez `callbackOnCollectedDelegate` włączone MDA niezarządzanego kodu kierowania jest usuwany, gdy pełnomocnik jest zbierany. Z `callbackOnCollectedDelegate` mda włączone, niezarządzany kod kierowanie nie jest natychmiast usuwany podczas pobierania pełnomocnika. Zamiast tego ostatnie 1000 wystąpień są domyślnie utrzymywane przy życiu i zmieniane, aby aktywować MDA po wywołaniu. Thunk jest ostatecznie usuwany po 1001 więcej marshaled delegatów są zbierane.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA raportuje nazwę typu delegata, który został zebrany przed wywołaniem zwrotnym próbowano na jego wskaźnik funkcji niezarządzane.  
  
## <a name="configuration"></a>Konfigurowanie  
 W poniższym przykładzie przedstawiono opcje konfiguracji aplikacji. Ustawia liczbę thunks MDA utrzymuje przy życiu do 1500. Wartość `listSize` domyślna to 1000, minimalna 50, a maksymalna 2000.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sytuację, która może aktywować ten MDA:  
  
```cpp
// Library.cpp : Defines the unmanaged entry point for the DLL application.  
#include "windows.h"  
#include "stdio.h"  
  
void (__stdcall *g_pfTarget)();  
  
void __stdcall Initialize(void __stdcall pfTarget())  
{  
    g_pfTarget = pfTarget;  
}  
  
void __stdcall Callback()  
{  
    g_pfTarget();  
}
```

```csharp
// C# Client  
using System;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public delegate void DCallback();  
  
    public static void Main()  
    {  
        new Entry();  
        Initialize(Target);  
        GC.Collect();  
        GC.WaitForPendingFinalizers();  
        Callback();  
    }  
  
    public static void Target()  
    {
    }  
  
    [DllImport("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Initialize(DCallback pfDelegate);  
  
    [DllImport ("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Callback();  
  
    ~Entry() { Console.Error.WriteLine("Entry Collected"); }  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)
