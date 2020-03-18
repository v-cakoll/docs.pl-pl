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
ms.openlocfilehash: 80c90254978495a58d228c4302eda84d6165c800
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138075"
---
# <a name="eventwaithandle"></a>EventWaitHandle
Klasa <xref:System.Threading.EventWaitHandle> umożliwia wątkom komunikowanie się ze sobą poprzez sygnalizację i oczekiwanie na sygnały. Zdarzenia wait uchwyty (również określane po prostu jako zdarzenia) są uchwyty oczekiwania, które mogą być sygnalizowane w celu zwolnienia jednego lub więcej wątków oczekiwania. Po sygnale uchwyt oczekiwania na zdarzenie jest resetowany ręcznie lub automatycznie. Klasa <xref:System.Threading.EventWaitHandle> może reprezentować dojście oczekiwania zdarzenia lokalnego (zdarzenie lokalne) lub nazwany dojście oczekiwania zdarzenia systemowego (nazwane zdarzenie lub zdarzenie systemowe, widoczne dla wszystkich procesów).  
  
> [!NOTE]
> Dojścia oczekiwania na zdarzenia nie są [zdarzeniami](../events/index.md).NET . Nie ma żadnych delegatów lub obsługi zdarzeń zaangażowanych. Słowo "zdarzenie" jest używane do ich opisania, ponieważ tradycyjnie były one określane jako zdarzenia systemu operacyjnego, a ponieważ akt sygnalizacji dojścia oczekiwania wskazuje na wątki oczekiwania, że wystąpiło zdarzenie.  
  
 Zarówno lokalne, jak i nazwane zdarzeń wait uchwyty <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> używać obiektów synchronizacji systemu, które są chronione przez otoki, aby upewnić się, że zasoby są zwalniane. Można użyć <xref:System.Threading.WaitHandle.Dispose%2A> metody, aby zwolnić zasoby natychmiast po zakończeniu przy użyciu obiektu.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Zdarzeń Wait Uchwyty, które resetują się automatycznie  
 Zdarzenie automatycznego resetowania można <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> utworzyć, <xref:System.Threading.EventWaitHandle> określając podczas tworzenia obiektu. Jak sama nazwa wskazuje, to zdarzenie synchronizacji resetuje się automatycznie po sygnale, po zwolnieniu pojedynczego wątku oczekiwania. Zasygnalizuj <xref:System.Threading.EventWaitHandle.Set%2A> zdarzenie, wywołując jego metodę.  
  
 Zdarzenia automatycznego resetowania są zwykle używane do zapewnienia wyłącznego dostępu do zasobu dla pojedynczego wątku w czasie. Wątek żąda zasobu, <xref:System.Threading.WaitHandle.WaitOne%2A> wywołując metodę. Jeśli żaden inny wątek nie trzyma dojście oczekiwania, metoda zwraca `true` i wątek wywołujący ma kontrolę nad zasobem.  
  
> [!IMPORTANT]
> Podobnie jak w przypadku wszystkich mechanizmów synchronizacji, należy upewnić się, że wszystkie ścieżki kodu czekać na odpowiedni uchwyt oczekiwania przed dostępem do chronionego zasobu. Synchronizacja wątków jest współpracy.  
  
 Jeśli zdarzenie automatycznego resetowania jest sygnalizowane, gdy żadne wątki nie czekają, pozostaje sygnalizowane, dopóki wątek nie spróbuje na niego czekać. Zdarzenie zwalnia wątek i natychmiast resetuje, blokując kolejne wątki.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Zdarzeń Wait Uchwyty, które resetują się ręcznie  
 Zdarzenie resetowania ręcznego można <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> utworzyć, <xref:System.Threading.EventWaitHandle> określając podczas tworzenia obiektu. Jak sama nazwa wskazuje, to zdarzenie synchronizacji musi zostać zresetowane ręcznie po jego zasygnalizowaniu. Dopóki nie zostanie zresetowany, wywołując jego <xref:System.Threading.EventWaitHandle.Reset%2A> metodę, wątki, które czekają na dojście zdarzenia, są natychmiast przetwarzane bez blokowania.  
  
 Zdarzenie ręcznego resetowania działa jak brama corral. Gdy zdarzenie nie jest sygnalizowane, wątki, które czekają na nim blokują, jak konie w corral. Gdy zdarzenie jest sygnalizowane, <xref:System.Threading.EventWaitHandle.Set%2A> wywołując jego metodę, wszystkie wątki oczekiwania są wolne do kontynuowania. Zdarzenie pozostaje sygnalizowane, <xref:System.Threading.EventWaitHandle.Reset%2A> dopóki jego metoda nie zostanie wywołana. To sprawia, że zdarzenie resetowania ręcznego idealnym sposobem na wstrzymanie wątków, które muszą poczekać, aż jeden wątek zakończy zadanie.  
  
 Podobnie jak konie pozostawiając corral, to wymaga czasu na zwolnionych wątków, które mają być zaplanowane przez system operacyjny i wznowić wykonywanie. Jeśli <xref:System.Threading.EventWaitHandle.Reset%2A> metoda jest wywoływana przed wznowieniem wykonywania wszystkich wątków, pozostałe wątki ponownie blokują. Które wątki wznawiają i które blokwątki zależą od losowych czynników, takich jak obciążenie systemu, liczba wątków oczekujących na harmonogram i tak dalej. Nie jest to problem, jeśli wątek, który sygnalizuje zdarzenie kończy się po sygnale, który jest najczęstszym wzorcem użycia. Jeśli chcesz, aby wątek, który zasygnalizował zdarzenie, aby rozpocząć nowe zadanie po wznowieniu wszystkich wątków oczekiwania, należy zablokować go, dopóki wszystkie wątki oczekiwania zostały wznowione. W przeciwnym razie masz stan wyścigu, a zachowanie kodu jest nieprzewidywalne.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Funkcje wspólne dla zdarzeń automatycznych i ręcznych  
 Zazwyczaj jeden lub więcej wątków <xref:System.Threading.EventWaitHandle> bloku na dopóki odblokowany wątek wywołuje <xref:System.Threading.EventWaitHandle.Set%2A> metodę, która zwalnia jeden z wątków oczekiwania (w przypadku zdarzeń automatycznego resetowania) lub wszystkie z nich (w przypadku zdarzeń resetowania ręcznego). Wątek może sygnalizować, <xref:System.Threading.EventWaitHandle> a następnie blokować na nim jako <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType> operację niepodzielną, wywołując metodę statyczną.  
  
 <xref:System.Threading.EventWaitHandle>obiekty mogą być używane <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> z metodami statycznymi i metodami. Ponieważ <xref:System.Threading.EventWaitHandle> klasy <xref:System.Threading.Mutex> i klasy <xref:System.Threading.WaitHandle>pochodzą z , można użyć obu klas z tych metod.  
  
### <a name="named-events"></a>Nazwane zdarzenia  
 System operacyjny Windows umożliwia uchwyty oczekiwania na zdarzenia mają nazwy. Zdarzenie o nazwie jest ogólnosystemowe. Oznacza to, że po utworzeniu nazwanego zdarzenia jest ono widoczne dla wszystkich wątków we wszystkich procesach. W związku z tym nazwane zdarzenia mogą służyć do synchronizowania działań procesów, a także wątków.  
  
 Można utworzyć <xref:System.Threading.EventWaitHandle> obiekt, który reprezentuje nazwane zdarzenie systemowe przy użyciu jednego z konstruktorów, który określa nazwę zdarzenia.  
  
> [!NOTE]
> Ponieważ nazwane zdarzenia są ogólnosystemowe, <xref:System.Threading.EventWaitHandle> istnieje możliwość posiadania wielu obiektów reprezentujących to samo nazwane zdarzenie. Za każdym razem, gdy wywołasz konstruktora lub <xref:System.Threading.EventWaitHandle.OpenExisting%2A> metodę, tworzony jest nowy <xref:System.Threading.EventWaitHandle> obiekt. Określanie tej samej nazwy wielokrotnie tworzy wiele obiektów, które reprezentują to samo nazwane zdarzenie.  
  
 Zaleca się ostrożność przy użyciu nazwanych zdarzeń. Ponieważ są one dla całego systemu, inny proces, który używa tej samej nazwy można zablokować wątki nieoczekiwanie. Złośliwy kod wykonywany na tym samym komputerze może użyć tego jako podstawy ataku typu "odmowa usługi".  
  
 Użyj zabezpieczeń kontroli dostępu, aby chronić <xref:System.Threading.EventWaitHandle> obiekt, który reprezentuje nazwane zdarzenie, najlepiej <xref:System.Security.AccessControl.EventWaitHandleSecurity> przy użyciu konstruktora, który określa obiekt. Można również zastosować zabezpieczenia kontroli <xref:System.Threading.EventWaitHandle.SetAccessControl%2A> dostępu przy użyciu tej metody, ale pozostawia to okno luki między czasem utworzenia uchwytu oczekiwania na zdarzenie a czasem, w którym jest on chroniony. Ochrona zdarzeń za pomocą zabezpieczeń kontroli dostępu pomaga zapobiegać złośliwym atakom, ale nie rozwiązuje problemu niezamierzonych kolizji nazw.  
  
> [!NOTE]
> W <xref:System.Threading.EventWaitHandle> przeciwieństwie do klasy <xref:System.Threading.AutoResetEvent> klasy <xref:System.Threading.ManualResetEvent> pochodne i może reprezentować tylko lokalne uchwyty oczekiwania. Nie mogą reprezentować nazwanych zdarzeń systemowych.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.EventWaitHandle>
- <xref:System.Threading.WaitHandle>
- <xref:System.Threading.AutoResetEvent>
- <xref:System.Threading.ManualResetEvent>
