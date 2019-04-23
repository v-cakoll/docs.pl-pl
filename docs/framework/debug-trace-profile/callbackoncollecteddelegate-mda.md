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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 459465064fe9db9f2f0aebb4153a3caea173af4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223644"
---
# <a name="callbackoncollecteddelegate-mda"></a>callbackOnCollectedDelegate MDA
`callbackOnCollectedDelegate` Zarządzanego Asystenta debugowania (MDA) jest włączone, jeśli obiekt delegowany jest przekazywane z kodu zarządzanego do kodu niezarządzanego jako wskaźnik funkcji i wywołanie zwrotne jest umieszczany na ten wskaźnik funkcji bezużyteczne po delegata.  
  
## <a name="symptoms"></a>Symptomy  
 Naruszenia zasad dostępu wystąpić, gdy próba wywołania kodu zarządzanego za pomocą wskaźników funkcji, które zostały uzyskane z zarządzanych obiektów delegowanych. Te błędy, podczas nie typowych błędów języka środowiska uruchomieniowego (języka wspólnego CLR), może wydawać się być tak, ponieważ naruszenie zasad dostępu odbywa się w kodzie CLR.  
  
 Błąd nie jest zgodne ze sobą. Czasami połączenie na wskaźnik funkcji zakończy się powodzeniem, a czasami kończy się niepowodzeniem. Błąd może wystąpić tylko pod dużym obciążeniem, lub na liczbę losową liczbę prób.  
  
## <a name="cause"></a>Przyczyna  
 Delegat, z którego została utworzona i udostępniana dla kodu niezarządzanego wskaźnik funkcji było bezużyteczne. Gdy składnik niezarządzanych próbuje wywołać na wskaźnik funkcji, generuje naruszenie zasad dostępu.  
  
 Błąd pojawia się losowych, ponieważ zależy podczas wyrzucania elementów bezużytecznych. Jeśli obiekt delegowany kwalifikuje się do kolekcji wyrzucania elementów bezużytecznych może wystąpić po wywołania zwrotnego i wywołanie powiedzie się. W pozostałym czasie wyrzucania elementów bezużytecznych występuje przed wywołania zwrotnego, wywołanie zwrotne generuje naruszenie zasad dostępu i zatrzymuje program.  
  
 Prawdopodobieństwo awarii zależy od czasu między marshaling delegata i wywołania zwrotnego na wskaźnik funkcji, jak i częstotliwość wyrzucania elementów bezużytecznych. Błąd jest sporadyczne, jeśli czas między marshaling delegata i wynikający z tego wywołania zwrotnego jest krótki. Jest to zazwyczaj tak, jeśli metoda niezarządzanego odbieranie wskaźnik funkcji nie jest zapisywany wskaźnik funkcji do późniejszego użycia, ale zamiast tego ponownie wywołuje na wskaźnik funkcji, aby ukończyć jej działania przed zwróceniem. Podobnie więcej wyrzucania elementów bezużytecznych wystąpić, gdy system jest mocno obciążony, co pozwala na bardziej prawdopodobne, że wyrzucania elementów bezużytecznych nastąpi przed wywołania zwrotnego.  
  
## <a name="resolution"></a>Rozwiązanie  
 Gdy obiekt delegowany został przekazany się jak wskaźnik funkcji niezarządzanej, moduł odśmiecania pamięci nie można śledzić jego okres istnienia. Zamiast tego kod musi przechowywać odwołanie do obiektu delegowanego okres istnienia wskaźnika funkcji niezarządzanej. Jednak zanim to zrobić, należy najpierw zidentyfikować delegata, który został zebrany. Gdy zdarzenie MDA jest aktywowane, zawiera nazwę typu delegata. Należy użyć tej nazwy do wyszukiwania wywołania kodu platformy lub podpisy COM, które przekazać delegata do kodu niezarządzanego. Naruszającym delegata jest przekazywana jeden z nich wywołania. Można również włączyć `gcUnmanagedToManaged` MDA do wymuszenia wyrzucania elementów bezużytecznych przed każdym wywołania zwrotnego w czasie wykonywania. Spowoduje to usunięcie niepewności wprowadzone przez wyrzucanie elementów bezużytecznych poprzez zapewnienie, że zawsze wyrzucania elementów bezużytecznych występuje przed wywołania zwrotnego. Wiesz, jakie delegata został zebrany, zmień swój kod, aby zachować odwołanie do delegata stronie zarządzanej okres istnienia wskaźnika zorganizowanej niezarządzanej funkcji.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Gdy obiekty delegowane są przekazywane jako wskaźniki funkcji, środowisko uruchomieniowe przydziela thunk, który wykonuje przejścia z niezarządzanych w zarządzanych. To wywołanie jest co kod niezarządzany wywołuje przed zarządzany obiekt delegowany na koniec jest wywoływany. Bez `callbackOnCollectedDelegate` MDA włączona, organizowanie kodu niezarządzanego jest usuwany po delegata są zbierane. Za pomocą `callbackOnCollectedDelegate` MDA włączona, niezarządzanych organizowanie kodu nie są natychmiast usuwane w przypadku delegata są zbierane. Zamiast tego ostatniego 1000 wystąpień są życiu domyślnie i zmienione w celu aktywowania MDA, gdy zostanie wywołana. Thunk został usunięty po pewnym czasie, gdy 1,001 bardziej zorganizowanej obiekty delegowane są zbierane.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA raporty nazwę typu delegata, który został zebrany przed podjęto próbę wywołania zwrotnego na swojego wskaźnika funkcji niezarządzanej.  
  
## <a name="configuration"></a>Konfiguracja  
 Poniższy przykład przedstawia opcje konfiguracji aplikacji. Ustawia liczbę sekcje Thunk, który MDA utrzymuje aktywność do 1500. Wartość domyślna `listSize` wartość wynosi 1000, minimum to 50, a wartość maksymalna to 2000.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sytuację, która może aktywować to zdarzenie MDA:  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
- [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
