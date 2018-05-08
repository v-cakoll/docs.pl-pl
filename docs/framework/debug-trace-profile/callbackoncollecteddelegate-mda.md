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
ms.openlocfilehash: 0aa9ecd357a192eba64cc14f8940b264461b5e74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="callbackoncollecteddelegate-mda"></a>callbackOnCollectedDelegate MDA
`callbackOnCollectedDelegate` Zarządzany Asystent debugowania (MDA) jest włączone, jeśli delegat jest przekazywane z kodu zarządzanego do kodu niezarządzanego jako wskaźnik funkcji i wywołanie zwrotne jest umieszczona na wskaźnik tej funkcji po bezużytecznych delegata.  
  
## <a name="symptoms"></a>Symptomy  
 Naruszenia zasad dostępu występują, jeśli próba wywołania wewnątrz kodu zarządzanego za pośrednictwem wskaźników funkcji, które zostały uzyskane z zarządzanych obiektów delegowanych. Te błędy podczas nie wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) usterki, mogą sprawiać, ponieważ naruszenie zasad dostępu występuje w kodzie CLR.  
  
 Błąd nie jest zgodne ze sobą. Czasami wywołania na wskaźnik funkcji zakończy się powodzeniem i czasami kończy się niepowodzeniem. Błąd może wystąpić tylko obciążona lub losową liczbę prób.  
  
## <a name="cause"></a>Przyczyna  
 Delegat, z którego została utworzona i ujawniony dla kodu niezarządzanego wskaźnika funkcji została wyrzucona jako element bezużyteczny. Próba wywołania na wskaźnik funkcji przez składnik niezarządzane generuje naruszenia zasad dostępu.  
  
 Błąd pojawia się losowych, ponieważ zależy po wystąpieniu wyrzucanie elementów bezużytecznych. Jeśli delegat jest uprawniona do kolekcji, wyrzucanie elementów bezużytecznych może wystąpić po wywołania zwrotnego i wywołanie zakończy się pomyślnie. W pozostałych godzinach wyrzucanie elementów bezużytecznych występuje przed wywołania zwrotnego, wywołania zwrotnego generuje naruszenia zasad dostępu i zatrzymuje program.  
  
 Prawdopodobieństwo wystąpienia błędu zależy od czasu między marshaling delegata i wywołania zwrotnego na wskaźnik funkcji, jak i częstotliwość odzyskiwania pamięci. Błąd jest sporadyczne, jeśli jest krótki czas między marshaling delegata i następujących wywołania zwrotnego. Jest to zwykle wielkość liter, jeśli metoda niezarządzanego odbieranie wskaźnik funkcji nie powoduje zapisania wskaźnik funkcji do późniejszego użycia, ale zamiast tego wywołuje na wskaźnik funkcji natychmiast, aby ukończyć jej działania przed zwróceniem. Podobnie więcej wyrzucania wystąpić, gdy system jest mocno obciążony, co pozwala na bardziej prawdopodobne, że przed wywołania zwrotnego nastąpi wyrzucania elementów bezużytecznych.  
  
## <a name="resolution"></a>Rozwiązanie  
 Po delegata organizowanego się jako wskaźnik funkcji niezarządzanej, moduł zbierający elementy bezużyteczne nie może śledzić jego okres istnienia. Zamiast tego kodu przez czas ich istnienia wskaźnika funkcji niezarządzanej przechowuje odwołanie do obiektu delegowanego. Jednak zanim można to zrobić, należy najpierw określić delegata, które zostały zebrane. Po aktywowaniu MDA zawiera nazwę typu obiektu delegowanego. Użyj tej nazwy do wyszukiwania wywołanie kodu platformy lub podpisy COM, które przekazać ten delegat do kodu niezarządzanego. Delegat ataku jest przekazywany za pomocą jednego z tych wywołań witryny. Można również włączyć `gcUnmanagedToManaged` MDA, aby wymusić wyrzucanie elementów bezużytecznych przed każdym wywołania zwrotnego w czasie wykonywania. Spowoduje to usunięcie niedokładność wprowadzone przez pamięci przez zapewnienie im występujący wyrzucania elementów bezużytecznych zawsze przed wywołania zwrotnego. Po sprawdzeniu, jakie delegata zostały zebrane, zmień swój kod, aby zachować odwołania do tego obiektu delegowanego po stronie zarządzanej przez czas ich istnienia wskaźnika funkcji niezarządzanej organizowane.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Jeśli obiekty delegowane są przekazywane jako wskaźników funkcji, środowisko uruchomieniowe przydziela thunk, który wykonuje przejścia z niezarządzanych w zarządzanych. Ta konwersja jest co niezarządzany kod wywołuje przed zarządzanej delegata na koniec jest wywoływana. Bez `callbackOnCollectedDelegate` MDA włączone, niezarządzany kod kierowania zostanie usunięta po są zbierane z obiektem delegowanym. Z `callbackOnCollectedDelegate` MDA włączone, niezarządzany kod kierowania nie są natychmiast usuwane podczas delegata są zbierane. Zamiast tego ostatniego 1000 wystąpień są utrzymywane domyślnie i zmienić aktywować MDA po wywołaniu. Thunk, zostanie ostatecznie usunięta po 1,001 więcej organizowane delegatów są zbierane.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA raporty nazwę typu delegata, który został zebrany zanim podjęto próbę wywołania zwrotnego na jego wskaźnika funkcji niezarządzanej.  
  
## <a name="configuration"></a>Konfiguracja  
 W poniższym przykładzie przedstawiono opcje konfiguracji aplikacji. Ustawia liczbę osadzeń, który MDA śledzi aktywności do 1500. Wartość domyślna `listSize` wynosi 1000, wartość minimalna to 50 i maksymalna to 2000.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sytuację, której można uaktywnić to zdarzenie MDA:  
  
```  
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
// ---------------------------------------------------  
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
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)  
 [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
