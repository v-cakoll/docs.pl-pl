---
title: EventWaitHandle
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], EventWaitHandle class
- EventWaitHandle class
- event wait handles [.NET Framework]
- threading [.NET Framework], cross-process synchronization
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20050eb3eb5fe41778d7a979f94cdd258650b33e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588928"
---
# <a name="eventwaithandle"></a>EventWaitHandle
<xref:System.Threading.EventWaitHandle> Klasa umożliwia wątków do komunikowania się ze sobą przez Sygnalizowanie i Oczekiwanie na sygnałów. Uchwyty oczekiwania na zdarzenie (zwaną także po prostu zdarzenia) są dojścia oczekiwania, które mogą być sygnalizowane, aby zwolnić jeden lub więcej wątków oczekujących. Po zasygnalizowania, dojścia oczekiwania jest resetowany, ręcznie lub automatycznie. <xref:System.Threading.EventWaitHandle> Klasa może reprezentować albo lokalnym zdarzeniem dojście oczekiwania (zdarzenie lokalne) lub zdarzeń o nazwie system poczekaj uchwytu (o nazwie zdarzenie lub systemu, widoczne dla wszystkich procesów).  
  
> [!NOTE]
>  Uchwyty oczekiwania na zdarzenie nie są .NET [zdarzenia](../events/index.md). Zaangażowanych bez delegatów i procedury obsługi zdarzeń. Słowo "zdarzenie" służy do opisywania ich ponieważ one mieć tradycyjnie zostało określone jako zdarzenia systemu operacyjnego, a czynność sygnalizowanie dojście oczekiwania wskazuje wątków oczekujących wystąpienia zdarzenia.  
  
 Zarówno uchwyty oczekiwania na zdarzenie lokalnych i nazwanych używać obiektów synchronizacji systemu, które są chronione przez <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> otoki, aby upewnić się, że zasoby są zwalniane. Możesz użyć <xref:System.Threading.WaitHandle.Dispose%2A> metody, aby zwolnić zasoby, natychmiast po zakończeniu korzystania z obiektu.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Uchwyty oczekiwania na zdarzenie, które automatycznie resetować  
 Utwórz zdarzenie zresetowaniu automatycznym, określając <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> po utworzeniu <xref:System.Threading.EventWaitHandle> obiektu. Jak sugeruje jej nazwa, to zdarzenie synchronizacji automatycznie po resetuje sygnalizowane po przy zwalnianiu pojedynczego wątku oczekiwania. Zasygnalizowania zdarzenia przez wywołanie jego <xref:System.Threading.EventWaitHandle.Set%2A> metody.  
  
 Automatyczne resetowanie zdarzenia zwykle są używane do zapewnienia wyłącznego dostępu do zasobu dla pojedynczego wątku w danym momencie. Wątek żąda zasobu, wywołując <xref:System.Threading.WaitHandle.WaitOne%2A> metody. Jeśli nie z innego wątku organizuje dojście oczekiwania, metoda zwraca `true` i Wątek wywołujący ma kontrolę nad zasobem.  
  
> [!IMPORTANT]
>  Podobnie jak w przypadku wszystkich mechanizmów synchronizacji, należy zadbać o wszystkie ścieżki kodu oczekiwania przed uzyskaniem dostępu do chronionego zasobu na dojście oczekiwania odpowiednie. Synchronizacja wątku jest wspólne.  
  
 Jeśli zdarzenie resetu automatycznego jest sygnalizowane, gdy nie ma wątków oczekujących, pozostaje sygnałowego aż wątek próby poczekaj na nim. Zdarzenie zwalnia wątku, a od razu resetuje, blokuje kolejnych wątków.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Uchwyty oczekiwania na zdarzenie, które ręcznie zresetować  
 Utwórz zdarzenie resetowania ręcznego, określając <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> po utworzeniu <xref:System.Threading.EventWaitHandle> obiektu. Jak sugeruje jej nazwa, to zdarzenie synchronizacji muszą zostać zresetowane ręcznie po ma zostały zasygnalizowane. Dopóki zostanie zresetowane, przez wywołanie jego <xref:System.Threading.EventWaitHandle.Reset%2A> metody, wątki, które oczekiwania na dojście zdarzenia bezzwłocznie ją kontynuować bez blokowania.  
  
 Działania zdarzenia, takie jak bramy corral resetowania ręcznego. Gdy zdarzenie nie jest sygnalizowane, zablokować wątki, które czekać na nim, takie jak konie w corral. Gdy zdarzenie jest sygnalizowane, przez wywołanie jego <xref:System.Threading.EventWaitHandle.Set%2A> metody wszystkich wątków oczekujących są bezpłatne kontynuować. Zdarzenie pozostaje sygnałowego aż do jego <xref:System.Threading.EventWaitHandle.Reset%2A> metoda jest wywoływana. To sprawia, że zdarzenie resetowania ręcznego idealny sposób, aby wstrzymać wątków, które musisz poczekać, aż jeden wątek kończy zadanie.  
  
 Podobnie jak konie opuszczania corral zajmuje trochę czasu wydana wątków do zaplanowania przez system operacyjny i wznowić wykonywanie. Jeśli <xref:System.Threading.EventWaitHandle.Reset%2A> metoda zostaje wywołana zanim wszystkie wątki zostały ponownie uruchomiono jego wykonywanie, ponownie zablokować pozostałych wątków. Które wznawianie wątków i który blok wątków zależy od losowe czynników, takich jak obciążenia w systemie, liczba wątków oczekuje dla harmonogramu i tak dalej. To nie jest problemem, jeśli wątek, który sygnalizuje zdarzenie kończy się po sygnalizowania, który jest najczęstszym wzorcem użycia. Jeśli chcesz, aby wątek, który sygnalizowane zdarzenie, aby po rozpoczęciu nowego zadania oczekiwania, które zostały wznowione wątków, należy zablokować dopóki wszystkie wątki oczekiwania zostały wznowione. W przeciwnym razie ma wyścigu i zachowanie kodu jest nieprzewidywalne.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Typowe funkcje do automatycznego i ręcznego zdarzeń  
 Zazwyczaj jeden lub więcej wątków zablokowane na <xref:System.Threading.EventWaitHandle> do momentu odblokowania wątek wywołuje <xref:System.Threading.EventWaitHandle.Set%2A> metody, która uwalnia jeden z wątków oczekujących (w przypadku zdarzeń zresetowaniu automatycznym) lub wszystkie z nich (w przypadku ręcznego resetowania zdarzenia). Wątek może sygnał <xref:System.Threading.EventWaitHandle> a następnie zablokować, jako operację niepodzielną, przez wywołanie statycznego <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> metody.  
  
 <xref:System.Threading.EventWaitHandle> obiekty mogą być używane z statycznej <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> i <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> metody. Ponieważ <xref:System.Threading.EventWaitHandle> i <xref:System.Threading.Mutex> obu klas pochodzić od <xref:System.Threading.WaitHandle>, można użyć obu klas przy użyciu tych metod.  
  
### <a name="named-events"></a>Zdarzenia o nazwie  
 System operacyjny Windows umożliwia uchwyty oczekiwania na zdarzenie mieć nazwy. Zdarzenia nazwanego jest całego systemu. Oznacza to, że po utworzeniu zdarzenia nazwanego jest widoczny dla wszystkich wątków we wszystkich procesów. W związku z tym o nazwie zdarzenia mogą służyć do synchronizowania działania procesów, a także wątków.  
  
 Możesz utworzyć <xref:System.Threading.EventWaitHandle> obiekt, który reprezentuje zdarzenie o nazwie system przy użyciu jednego z konstruktorów, które określa nazwę zdarzenia.  
  
> [!NOTE]
>  Ponieważ zdarzenia o nazwie całego systemu, istnieje możliwość wielu <xref:System.Threading.EventWaitHandle> obiekty reprezentujące takie same nazwanego zdarzenia. Każdorazowo wywołać konstruktora, lub <xref:System.Threading.EventWaitHandle.OpenExisting%2A> metodę, nowe <xref:System.Threading.EventWaitHandle> obiekt zostanie utworzony. Określenie tej samej nazwie wielokrotnie tworzy wiele obiektów, które reprezentują te same zdarzenia nazwanego.  
  
 Jest zachowanie ostrożności przy użyciu nazwę events. Ponieważ są one całego systemu, inny proces, który używa tej samej nazwie może zablokować wątki nieoczekiwanie. Złośliwy kod, wykonania na tym samym komputerze może wykorzystać tę podstawę ataku typu "odmowa usługi".  
  
 Umożliwia kontrolę dostępu, aby chronić <xref:System.Threading.EventWaitHandle> obiekt, który najlepiej reprezentuje zdarzenia nazwanego, za pomocą konstruktora, który określa <xref:System.Security.AccessControl.EventWaitHandleSecurity> obiektu. Można również stosować przy użyciu zabezpieczeń kontroli dostępu <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> metody, ale pozostawia oknem lukę między czas dojście oczekiwania zdarzeń jest tworzona i jest chroniony. Ochrona zdarzenia przy użyciu kontroli dostępu zabezpieczeń zapobiega złośliwe ataki, ale nie rozwiązuje problemu Kolizje nazw niezamierzone.  
  
> [!NOTE]
>  W odróżnieniu od <xref:System.Threading.EventWaitHandle> klasy, klasy pochodne <xref:System.Threading.AutoResetEvent> i <xref:System.Threading.ManualResetEvent> można tylko lokalne reprezentują uchwyty oczekiwania. Nie stanowią one zdarzenia systemowe nazwanych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.EventWaitHandle>
- <xref:System.Threading.WaitHandle>
- <xref:System.Threading.AutoResetEvent>
- <xref:System.Threading.ManualResetEvent>
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
