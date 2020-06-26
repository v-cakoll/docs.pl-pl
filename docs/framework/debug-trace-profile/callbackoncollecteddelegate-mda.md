---
title: callbackOnCollectedDelegate MDA
description: Zapoznaj się z asystentem debugowania zarządzanego w programie callbackOnCollectedDelegate (MDA) w programie .NET, który jest wywoływany, gdy wywołanie zwrotne występuje, gdy obiekt delegowany zostanie wyrzucony.
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
ms.openlocfilehash: 32f02a4e65455f11f3bfa9260caae8b4e48f494e
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416034"
---
# <a name="callbackoncollecteddelegate-mda"></a>callbackOnCollectedDelegate MDA
`callbackOnCollectedDelegate`Asystent debugowania zarządzanego (MDA) jest aktywowany, jeśli delegat jest zorganizowany z zarządzanego do niezarządzanego kodu jako wskaźnik funkcji, a wywołanie zwrotne jest umieszczane na tym wskaźniku funkcji, gdy delegat został pobrany jako bezużyteczny.  
  
## <a name="symptoms"></a>Objawy  
 Podczas próby wywołania kodu zarządzanego za pomocą wskaźników funkcji uzyskanych z zarządzanych delegatów nastąpiły naruszenia zasad dostępu. Te błędy, podczas gdy nie występują usterki środowiska uruchomieniowego języka wspólnego (CLR), mogą wydawać się tak, ponieważ w kodzie CLR występuje naruszenie zasad dostępu.  
  
 Błąd nie jest spójny; Czasami wywołanie funkcji powiedzie się i czasami kończy się niepowodzeniem. Awaria może wystąpić tylko przy dużym obciążeniu lub losowej liczbie prób.  
  
## <a name="cause"></a>Przyczyna  
 Delegat, z którego został utworzony wskaźnik funkcji i ujawniony w kodzie niezarządzanym, został odrzucony. Gdy składnik niezarządzany próbuje wywołać wskaźnik funkcji, generuje naruszenie zasad dostępu.  
  
 Błąd pojawia się losowo, ponieważ zależy od momentu wyrzucania elementów bezużytecznych. Jeśli delegat kwalifikuje się do kolekcji, wyrzucanie elementów bezużytecznych może wystąpić po wywołaniu wywołania zwrotnego i wywołaniu. W innych przypadkach wyrzucanie elementów bezużytecznych występuje przed wywołaniem zwrotnym, wywołanie zwrotne generuje naruszenie zasad dostępu, a program zostanie zatrzymany.  
  
 Prawdopodobieństwo wystąpienia błędu zależy od czasu między kierowaniem delegata i wywołaniem zwrotnym na wskaźniku funkcji, a także częstotliwością wyrzucania elementów bezużytecznych. Awaria jest sporadyczna, jeśli czas między kierowaniem delegata i wynikający z wywołania zwrotnego jest krótki. Zwykle jest to przypadek, jeśli niezarządzana Metoda otrzymująca wskaźnik funkcji nie zapisuje wskaźnika funkcji do późniejszego użycia, ale zamiast tego ponownie wywołuje wskaźnik funkcji, aby zakończyć operację przed zwróceniem. Podobnie więcej wyrzucania elementów bezużytecznych występuje, gdy system jest mocno obciążony, co sprawia, że wyrzucanie elementów bezużytecznych zostanie przeprowadzone przed wywołaniem zwrotnym.  
  
## <a name="resolution"></a>Rozwiązanie  
 Gdy delegat został zorganizowany jako wskaźnik funkcji niezarządzanej, Moduł wyrzucania elementów bezużytecznych nie może śledzić swojego okresu istnienia. Zamiast tego kod musi przechowywać odwołanie do delegata dla okresu istnienia wskaźnika funkcji niezarządzanej. Jednak przed wykonaniem tej czynności należy najpierw określić, który delegat został zebrany. Gdy zdarzenie MDA zostanie aktywowane, zawiera nazwę typu delegata. Użyj tej nazwy, aby przeszukać swój kod dla wywołania platformy lub sygnatur COM, które są przekazywane przez delegata do kodu niezarządzanego. Nieprawidłowy delegat jest przepuszczany przez jedną z tych lokacji wywołań. Można również włączyć funkcję `gcUnmanagedToManaged` MDA, aby wymusić wyrzucanie elementów bezużytecznych przed każdym wywołaniem zwrotnym do środowiska uruchomieniowego. Spowoduje to usunięcie niepewności wprowadzonej przez wyrzucanie elementów bezużytecznych przez zapewnienie, że wyrzucanie elementów bezużytecznych zawsze występuje przed wywołaniem zwrotnym. Po uzyskaniu informacji o tym, który delegat został zebrany, Zmień kod, aby zachować odwołanie do tego delegata po stronie zarządzanej na potrzeby okresu istnienia organizowanego wskaźnika funkcji niezarządzanej.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Gdy Delegaty są organizowane jako wskaźniki funkcji, środowisko uruchomieniowe przydziela element thunk, który powoduje, że przejście z niezarządzanego do zarządzanego. Thunk jest to, co faktycznie wywołuje kod niezarządzany, zanim zarządzany delegat jest ostatecznie wywoływany. Bez `callbackOnCollectedDelegate` włączonego MDA, niezarządzany kod kierujący jest usuwany podczas zbierania delegata. `callbackOnCollectedDelegate`Po włączeniu trybu MDA niezarządzany kod kierujący nie jest natychmiast usuwany po zebraniu delegata. Zamiast tego ostatnie wystąpienia 1 000 są utrzymywane domyślnie i zmieniane w celu aktywowania MDA po wywołaniu. Thunk jest ostatecznie usuwana po 1 001 większej liczby delegatów zorganizowanych.  
  
## <a name="output"></a>Dane wyjściowe  
 Zdarzenie MDA raportuje nazwę typu delegata, który został zebrany przed podjęciem próby wywołania zwrotnego na niezarządzanym wskaźniku funkcji.  
  
## <a name="configuration"></a>Konfiguracja  
 W poniższym przykładzie przedstawiono opcje konfiguracji aplikacji. Ustawia liczbę sekcje thunk, że zdarzenie MDA utrzymuje aktywność do 1 500. Wartość domyślna `listSize` to 1 000, minimum to 50, a maksymalna to 2 000.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sytuację, w której można aktywować to MDA:  
  
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
