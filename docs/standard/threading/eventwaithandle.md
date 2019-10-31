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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138075"
---
# <a name="eventwaithandle"></a>EventWaitHandle
Klasa <xref:System.Threading.EventWaitHandle> pozwala wątkom komunikować się ze sobą przez sygnalizowanie i przez oczekiwanie na sygnały. Dojścia do oczekiwania zdarzeń (nazywane również tylko zdarzeniami) są dojściami oczekiwania, które mogą być sygnalizowane, aby zwolnić jeden lub więcej oczekujących wątków. Po zasygnalizowaniu dojście do oczekiwania na zdarzenie jest resetowane ręcznie lub automatycznie. Klasa <xref:System.Threading.EventWaitHandle> może reprezentować albo lokalnego uchwytu oczekiwania na zdarzenie (zdarzenie lokalne) lub nazwanego uchwytu oczekiwania zdarzenia systemu (nazwanego zdarzenia lub zdarzenia systemowe, widoczne dla wszystkich procesów).  
  
> [!NOTE]
> Uchwyty oczekiwania zdarzeń nie są [zdarzeniami](../events/index.md)platformy .NET. Brak obiektów delegowanych lub programów obsługi zdarzeń. Słowo "Event" służy do opisywania ich, ponieważ tradycyjnie nazywa się zdarzeniami systemu operacyjnego, a ponieważ czynność sygnalizująca dojście oczekiwania wskazuje na oczekujące wątki, które wystąpiły zdarzenie.  
  
 Zarówno lokalne, jak i nazwane usługi oczekują na używanie obiektów synchronizacji systemu, które są chronione przez otoki <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle>, aby upewnić się, że zasoby zostały wydane. Możesz użyć metody <xref:System.Threading.WaitHandle.Dispose%2A>, aby zwolnić zasoby natychmiast po zakończeniu korzystania z obiektu.  
  
## <a name="event-wait-handles-that-reset-automatically"></a>Uchwyty oczekiwania zdarzeń, które są resetowane automatycznie  
 Można utworzyć automatyczne Resetowanie zdarzenia przez określenie <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> podczas tworzenia obiektu <xref:System.Threading.EventWaitHandle>. Ponieważ jego nazwa oznacza, to zdarzenie synchronizacji jest resetowane automatycznie po zasygnalizowaniu, po zwolnieniu pojedynczego wątku oczekującego. Sygnalizowanie zdarzenia przez wywołanie jego metody <xref:System.Threading.EventWaitHandle.Set%2A>.  
  
 Zdarzenia automatycznego resetowania są zwykle używane do zapewniania wyłącznego dostępu do zasobu dla pojedynczego wątku w danym momencie. Wątek żąda zasobu przez wywołanie metody <xref:System.Threading.WaitHandle.WaitOne%2A>. Jeśli żaden inny wątek nie utrzymuje dojścia oczekiwania, metoda zwraca `true` i wątek wywołujący ma kontrolę nad zasobem.  
  
> [!IMPORTANT]
> Podobnie jak w przypadku wszystkich mechanizmów synchronizacji, przed uzyskaniem dostępu do chronionego zasobu należy upewnić się, że wszystkie ścieżki kodu oczekują na odpowiednie dojście oczekiwania. Synchronizacja wątków jest spółdzielnią.  
  
 Jeśli automatyczne resetowanie zostanie sygnalizowane, gdy żaden wątek nie oczekuje, pozostaje zasygnalizowani do momentu, gdy wątki spróbuje go zaczekać. Zdarzenie zwalnia wątek i natychmiast resetuje, blokując kolejne wątki.  
  
## <a name="event-wait-handles-that-reset-manually"></a>Uchwyty oczekiwania zdarzeń resetowania ręcznie  
 Można utworzyć zdarzenie resetowania ręcznego, określając <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> podczas tworzenia obiektu <xref:System.Threading.EventWaitHandle>. Ponieważ jego nazwa to oznacza, to zdarzenie synchronizacji należy zresetować ręcznie po zasygnalizowaniu. Dopóki nie zostanie zresetowane, wywołując jego metodę <xref:System.Threading.EventWaitHandle.Reset%2A>, wątki, które czekają na obsługę zdarzeń, przejdą natychmiast bez blokowania.  
  
 Zdarzenie resetowania ręcznego działa jak Brama Corral. Gdy zdarzenie nie jest sygnalizowane, wątki czekające na blok IT, takie jak konie w Corral. Po zasygnalizowaniu zdarzenia, wywołując jego metodę <xref:System.Threading.EventWaitHandle.Set%2A>, wszystkie oczekujące wątki można wykonać bezpłatnie. Zdarzenie pozostaje sygnalizowane do momentu wywołania metody <xref:System.Threading.EventWaitHandle.Reset%2A>. Powoduje to, że zdarzenie resetowania ręcznego jest idealnym sposobem przechowywania wątków, które muszą czekać, aż jeden wątek zakończy zadanie.  
  
 Podobnie jak konie opuszczające Corral, czas potrzebny na zaplanowanie opublikowanych wątków przez system operacyjny i wznowienie wykonywania. Jeśli metoda <xref:System.Threading.EventWaitHandle.Reset%2A> jest wywoływana przed wznowieniem wykonywania wszystkich wątków, pozostałe wątki są ponownie blokowane. Które wątki są wznawiane i które wątki są zależne od losowych czynników, takich jak obciążenie systemu, liczba wątków oczekujących na harmonogram itd. Nie jest to problem, jeśli wątek, który sygnalizuje zakończenie zdarzenia po zasygnalizowaniu, jest najbardziej typowym wzorcem użycia. Jeśli chcesz, aby wątek zgłosił zdarzenie, aby rozpocząć nowe zadanie po wznowieniu wszystkich oczekujących wątków, należy je zablokować do momentu wznowienia wszystkich oczekujących wątków. W przeciwnym razie masz sytuację wyścigu, a zachowanie kodu jest nieprzewidywalne.  
  
## <a name="features-common-to-automatic-and-manual-events"></a>Funkcje wspólne dla zdarzeń automatycznych i ręcznych  
 Zwykle co najmniej jeden wątek jest blokowany na <xref:System.Threading.EventWaitHandle> do momentu wywołania przez odblokowany wątek metody <xref:System.Threading.EventWaitHandle.Set%2A>, która zwalnia jeden z oczekujących wątków (w przypadku zdarzeń resetowania automatycznego) lub wszystkich (w przypadku zdarzeń resetowania ręcznego). Wątek może sygnalizować <xref:System.Threading.EventWaitHandle>, a następnie blokować go, jako operację niepodzielną, wywołując metodę static <xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType>.  
  
 obiektów <xref:System.Threading.EventWaitHandle> można używać z metodami statycznymi <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> i <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>. Ponieważ klasy <xref:System.Threading.EventWaitHandle> i <xref:System.Threading.Mutex> pochodzą z <xref:System.Threading.WaitHandle>, można użyć obu klas z tymi metodami.  
  
### <a name="named-events"></a>Nazwane zdarzenia  
 System operacyjny Windows zezwala na korzystanie z nazw uchwytów oczekiwania na zdarzenia. Nazwane zdarzenie to system Wide. Oznacza to, że po utworzeniu nazwanego zdarzenia jest ono widoczne dla wszystkich wątków we wszystkich procesach. W ten sposób nazwane zdarzenia mogą służyć do synchronizowania działań procesów oraz wątków.  
  
 Można utworzyć obiekt <xref:System.Threading.EventWaitHandle>, który reprezentuje nazwane zdarzenie systemowe przy użyciu jednego z konstruktorów, które określają nazwę zdarzenia.  
  
> [!NOTE]
> Ze względu na to, że nazwane zdarzenia są systemem szerokim, możliwe jest posiadanie wielu <xref:System.Threading.EventWaitHandle> obiektów, które reprezentują to samo nazwane zdarzenie. Za każdym razem, gdy wywołujesz konstruktora lub metodę <xref:System.Threading.EventWaitHandle.OpenExisting%2A>, tworzony jest nowy obiekt <xref:System.Threading.EventWaitHandle>. Wielokrotne określenie tej samej nazwy powoduje utworzenie wielu obiektów reprezentujących to samo nazwane zdarzenie.  
  
 Należy zachować ostrożność przy użyciu nazwanych zdarzeń. Ponieważ są one całego systemu, inny proces, który używa tej samej nazwy, może blokować nieoczekiwane wątki. Złośliwy kod wykonywany na tym samym komputerze może być używany jako podstawa ataku typu "odmowa usługi".  
  
 Zabezpieczenia kontroli dostępu umożliwiają ochronę obiektu <xref:System.Threading.EventWaitHandle>, który reprezentuje nazwane zdarzenie, najlepiej przy użyciu konstruktora, który określa obiekt <xref:System.Security.AccessControl.EventWaitHandleSecurity>. Możesz również zastosować zabezpieczenia kontroli dostępu przy użyciu metody <xref:System.Threading.EventWaitHandle.SetAccessControl%2A>, ale powoduje to pozostawienie okna luk w zabezpieczeniach między momentem utworzenia uchwytu oczekiwania na zdarzenie i czasu jego ochrony. Ochrona zdarzeń z zabezpieczeniami kontroli dostępu pomaga zapobiegać złośliwym atakom, ale nie rozwiązuje problemu przypadkowych kolizji nazw.  
  
> [!NOTE]
> W przeciwieństwie do klasy <xref:System.Threading.EventWaitHandle>, klasy pochodne <xref:System.Threading.AutoResetEvent> i <xref:System.Threading.ManualResetEvent> mogą reprezentować tylko lokalne dojścia oczekiwania. Nie mogą reprezentować nazwanych zdarzeń systemowych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.EventWaitHandle>
- <xref:System.Threading.WaitHandle>
- <xref:System.Threading.AutoResetEvent>
- <xref:System.Threading.ManualResetEvent>
