---
title: EventWaitHandle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], EventWaitHandle class
- EventWaitHandle class
- event wait handles [.NET Framework]
- threading [.NET Framework], cross-process synchronization
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 665676a25aea48388ba01b8028af00049b113f2b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="eventwaithandle"></a>EventWaitHandle
<xref:System.Threading.EventWaitHandle> Klasa umożliwia wątków, aby komunikować się ze sobą za pomocą sygnalizacji i Oczekiwanie na sygnały. Uchwyty oczekiwania na zdarzenie (zwaną także po prostu zdarzeń) to dojścia oczekiwania, które można zasygnalizować aby zwolnić jeden lub więcej wątków oczekujących. Po zostanie zasygnalizowane dojścia oczekiwania jest resetowany ręcznie lub automatycznie. <xref:System.Threading.EventWaitHandle> Klasa może reprezentować albo lokalnego oczekiwania obsługi zdarzenia (zdarzenie lokalnego) lub zdarzenia o nazwie systemu Zaczekaj dojścia (o nazwie zdarzenia lub zdarzeń systemowych są widoczne dla wszystkich procesów).  
  
> [!NOTE]
>  Uchwyty oczekiwania na zdarzenie nie są zdarzenia, w tym sensie, zazwyczaj przeznaczone przez wyrazie w programie .NET Framework. Nie ma żadnych obiektów delegowanych ani programów obsługi zdarzeń związane. Słowa "event" służy do opisywania je, ponieważ one mieć tradycyjnie zostały określone jako zdarzenia systemu operacyjnego, a czynność sygnalizowania dojście oczekiwania wskazuje wątków oczekujących wystąpienia zdarzenia.  
  
 Zarówno uchwyty oczekiwania na zdarzenie nazwane i lokalnych użyć obiektów synchronizacji systemu, które są chronione przez <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> otoki, aby upewnić się, że zasoby są wydawane. Można użyć <xref:System.Threading.WaitHandle.Dispose%2A> metody, aby zwolnić zasoby natychmiast po zakończeniu przy użyciu obiektu.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Uchwyty oczekiwania na zdarzenie, które automatycznie resetować  
 Utwórz zdarzenie automatycznego resetowania, określając <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> podczas tworzenia <xref:System.Threading.EventWaitHandle> obiektu. Jak jego nazwa wskazuje, to zdarzenie synchronizacji automatycznie po resetuje sygnalizowane po zwalniania pojedynczego wątku oczekiwania. Sygnału zdarzenia przez wywołanie jego <xref:System.Threading.EventWaitHandle.Set%2A> metody.  
  
 Automatyczne resetowanie zdarzenia zwykle są używane do zapewnienia wyłącznego dostępu do zasobu dla pojedynczego wątku w czasie. Wątek żąda zasobu, wywołując <xref:System.Threading.WaitHandle.WaitOne%2A> metody. Jeśli nie inne wątku wstrzymał dojście oczekiwania, metoda zwraca `true` i wątku wywołującym ma kontrolę zasobu.  
  
> [!IMPORTANT]
>  Podobnie jak w przypadku wszystkich mechanizmów synchronizacji, należy się upewnić, czy wszystkie ścieżki kodu oczekiwanie na dojście odpowiednie oczekiwania przed uzyskaniem dostępu do chronionego zasobu. Synchronizacja wątku jest współpracy.  
  
 W przypadku automatycznego resetowania zdarzenie jest sygnalizowane, gdy nie ma wątków oczekujących, pozostaje sygnałowego dopóki wątku próbuje czekać na nim. Zdarzenie zwalnia wątku i resetuje natychmiast, blokowanie kolejnych wątków.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Uchwyty oczekiwania na zdarzenie, które ręcznie zresetować  
 Utwórz zdarzenie z resetowaniem ręcznym, określając <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> podczas tworzenia <xref:System.Threading.EventWaitHandle> obiektu. Jak jego nazwa wskazuje, to zdarzenie synchronizacji można ręcznie zresetować po ma zostać sygnalizowane. Dopóki zostanie zresetowane, wywołując jego <xref:System.Threading.EventWaitHandle.Reset%2A> metody wątków oczekiwania na dojście zdarzenia bezzwłocznie ją kontynuować bez blokowania.  
  
 Zdarzenie działania takie jak brama corral resetowania ręcznego. Gdy zdarzenie nie zostanie zasygnalizowane, wątków, które Zaczekaj na jej zablokować, takie jak konie w corral. Gdy zdarzenie jest sygnalizowane, wywołując jego <xref:System.Threading.EventWaitHandle.Set%2A> metody, wszystkich wątków oczekujących są wolne kontynuować. Zdarzenie pozostaje sygnałowego aż do jego <xref:System.Threading.EventWaitHandle.Reset%2A> metoda jest wywoływana. Dzięki temu zdarzeń resetowania ręcznego idealny do przechowywania zapasowej wątków, które trzeba czekać na zakończenie zadania, jeden wątek.  
  
 Jak konie, pozostawiając corral czas wydanych wątków do zaplanowania przez system operacyjny i wznowić wykonywanie. Jeśli <xref:System.Threading.EventWaitHandle.Reset%2A> metoda jest wywoływana przed wszystkie wątki zostały wznowił pracę, pozostałe wątki ponownie zablokować. Które wznawianie wątków i który blok wątków zależy od losowe czynniki, takie jak obciążenia w systemie, to liczba wątków oczekiwania dla harmonogramu i tak dalej. Nie jest to problem, jeśli wątek, który sygnalizuje zdarzenie kończy się po zasygnalizowaniu, który jest najbardziej typowych wzorca użycia. Jeśli chcesz wątku, który sygnalizuje zdarzeń, aby rozpocząć nowego zadania po wszystkich oczekujących, który podjęto wątków musi zablokować dopóki podjęto wszystkich wątków oczekujących. W przeciwnym razie ma wyścigu i jest nieprzewidywalne zachowanie kodu.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Wspólne funkcje automatycznej i ręcznej zdarzenia  
 Zazwyczaj zablokować co najmniej jeden wątek na <xref:System.Threading.EventWaitHandle> do momentu wywołania wątku odblokowany <xref:System.Threading.EventWaitHandle.Set%2A> metodę, która udostępnia jeden z wątków oczekujących (w przypadku zdarzeń automatycznego resetowania) lub wszystkie z nich (w przypadku ręcznego resetowania zdarzeń). Wątek może sygnalizować <xref:System.Threading.EventWaitHandle> a następnie zablokować, jako operacją niepodzielną, wywołując statycznych <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> metody.  
  
 <xref:System.Threading.EventWaitHandle>obiekty mogą być używane z statycznych <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> i <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> metody. Ponieważ <xref:System.Threading.EventWaitHandle> i <xref:System.Threading.Mutex> pochodną klasy zarówno <xref:System.Threading.WaitHandle>, obie klasy można używać z tych metod.  
  
### <a name="named-events"></a>Zdarzenia o nazwie  
 System operacyjny Windows umożliwia uchwyty oczekiwania na zdarzenie mieć nazwy. Nazwane zdarzenie jest całym systemie. Oznacza to, że po utworzeniu zdarzenia o nazwie jest widoczne dla wszystkich wątków w wszystkich procesów. W związku z tym nazwanego zdarzenia mogą służyć do synchronizowania działania procesów, a także wątków.  
  
 Można utworzyć <xref:System.Threading.EventWaitHandle> obiekt, który reprezentuje zdarzenia o nazwie systemu za pomocą jednego z konstruktorów, które określa nazwę zdarzenia.  
  
> [!NOTE]
>  Ponieważ nazwanego zdarzenia to w całym systemie istnieje możliwość wielu <xref:System.Threading.EventWaitHandle> zdarzenia o nazwie obiekty reprezentujące takie same. Zawsze należy wywołać konstruktora, lub <xref:System.Threading.EventWaitHandle.OpenExisting%2A> metoda, nowy <xref:System.Threading.EventWaitHandle> tworzony jest obiekt. Określenie tej samej nazwie wielokrotnie tworzy wiele obiektów, które reprezentują tego samego zdarzenia nazwanego.  
  
 Zalecane jest ostrożność przy użyciu o nazwie zdarzenia. Ponieważ są one całym systemie, inny proces, który używa tej samej nazwie może zablokować użytkownika wątków nieoczekiwanie. Złośliwy kod na tym samym komputerze może wykorzystać tę podstawę ataku typu "odmowa usługi".  
  
 Umożliwia kontrolę dostępu, aby chronić <xref:System.Threading.EventWaitHandle> obiekt, który reprezentuje nazwanego zdarzenia, najlepiej przy użyciu konstruktora, który określa <xref:System.Security.AccessControl.EventWaitHandleSecurity> obiektu. Można także zastosować dla zabezpieczeń kontroli dostępu przy użyciu opcji <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> metody, ale pozostawia okno luki w zabezpieczeniach między czas, zostanie utworzony uchwyt oczekiwania zdarzeń i jest on chroniony. Ochrona zdarzeń przy użyciu kontroli dostępu zabezpieczeń pomaga zapobiegać złośliwe ataki, ale nie rozwiązuje problemu konflikty nazw przypadkowe.  
  
> [!NOTE]
>  W odróżnieniu od <xref:System.Threading.EventWaitHandle> klasy, klasy pochodne <xref:System.Threading.AutoResetEvent> i <xref:System.Threading.ManualResetEvent> można tylko lokalne reprezentują uchwyty oczekiwania. Nie można reprezentują zdarzenia o nazwie system.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
