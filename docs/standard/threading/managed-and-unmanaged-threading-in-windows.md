---
title: Zarządzana i niezarządzana wątkowość w systemie Windows
ms.date: 10/24/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], unmanaged
- threading [.NET Framework], managed
- threading [.NET], managed
- threads and fibers [.NET]
- managed threading
ms.assetid: 4fb6452f-c071-420d-9e71-da16dee7a1eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da32d514b19424487cebc1d113388cfa9a2dbdf0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913228"
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Wątki zarządzane i niezarządzane w systemie Windows

Zarządzanie wszystkimi wątkami odbywa się za pomocą <xref:System.Threading.Thread> klasy, w tym wątków utworzonych przez środowisko uruchomieniowe języka wspólnego oraz utworzonych poza środowiskiem uruchomieniowym, które wprowadzają kod w środowisku zarządzanym. Środowisko uruchomieniowe monitoruje wszystkie wątki w swoim procesie, które kiedykolwiek wykonywały kod w zarządzanym środowisku wykonywania. Nie śledzi żadnych innych wątków. Wątki mogą wprowadzać zarządzane środowisko wykonawcze za pomocą międzyoperacyjności modelu COM (ponieważ środowisko uruchomieniowe udostępnia obiekty zarządzane jako obiekty COM w niezarządzanym świecie), funkcję COM [DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject) i wywołanie platformy.  
  
 Gdy niezarządzany wątek przejdzie do środowiska uruchomieniowego za pomocą, na przykład otoki możliwej do odnalezienia com, system sprawdza, czy Magazyn lokalny wątku tego <xref:System.Threading.Thread> wątku szuka wewnętrznego obiektu zarządzanego. Jeśli zostanie znaleziony, środowisko uruchomieniowe już wie o tym wątku. Jeśli jednak nie można znaleźć jednego z nich, środowisko uruchomieniowe kompiluje nowy <xref:System.Threading.Thread> obiekt i zainstaluje je w magazynie lokalnym wątku tego wątku.  
  
 W zarządzanych wątkach <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> jest stabilna identyfikacja zarządzanego wątku. W przypadku okresu istnienia wątku nie będzie kolizja z wartością z dowolnego innego wątku, niezależnie od domeny aplikacji, z której ma zostać uzyskana ta wartość.  
  
> [!NOTE]
> **ThreadID** systemu operacyjnego nie ma stałej relacji z zarządzanym wątkiem, ponieważ niezarządzany host może kontrolować relacje między wątki zarządzane i niezarządzane. W przypadku zaawansowanego hosta można użyć interfejsu API Fiber do zaplanowania wielu zarządzanych wątków względem tego samego wątku systemu operacyjnego lub przenoszenia zarządzanego wątku między różnymi wątkami systemu operacyjnego.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Mapowanie z wątku Win32 na zarządzane wątkowość

 W poniższej tabeli zawarto Mapowanie elementów wątków Win32 do ich przybliżonych odpowiedników środowiska uruchomieniowego. Należy zauważyć, że to mapowanie nie reprezentuje identycznych funkcji. Na przykład **TerminateThread** nie wykonuje klauzul **finally** ani nie zwalnia zasobów i nie można go zablokować. Jednak wykonuje cały kod wycofania, przejmuje wszystkie zasoby i może zostać odmówiony przy użyciu <xref:System.Threading.Thread.ResetAbort%2A>. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Pamiętaj, aby dokładnie zapoznać się z dokumentacją przed wprowadzeniem założeń dotyczących funkcjonalności.  
  
|W systemie Win32|W środowisku uruchomieniowym języka wspólnego|  
|--------------|------------------------------------|  
|**CreateThread**|Kombinacja **wątku** i<xref:System.Threading.ThreadStart>|  
|**TerminateThread**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**SuspendThread**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**ResumeThread**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**Chodzenia**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|**WaitForSingleObject** w obsłudze wątku|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**ExitThread**|Brak równoważnej|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Brak równoważnej|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Brak równoważnej|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|Blisko **CoInitializeEx** (ole32. BIBLIOTECE|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Zarządzane wątki i apartamentach COM

Wątek zarządzany może być oznaczony, aby wskazać, że będzie hostować Apartament jednowątkowy lub [](/windows/desktop/com/multithreaded-apartments) wielowątkowy. [](/windows/desktop/com/single-threaded-apartments) (Aby uzyskać więcej informacji na temat architektury wątkowości COM, zobacz [procesy, wątki i apartamentach](/windows/desktop/com/processes--threads--and-apartments)). Metody <xref:System.Threading.Thread.GetApartmentState%2A>, <xref:System.Threading.Thread.SetApartmentState%2A> ,i<xref:System.Threading.Thread.TrySetApartmentState%2A> klasy zwracają i przypisują stan Apartment wątku. <xref:System.Threading.Thread> Jeśli stan nie został ustawiony, <xref:System.Threading.Thread.GetApartmentState%2A> zwraca. <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>  
  
 Właściwość można ustawić tylko wtedy, gdy wątek jest w <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> stanie; można ją ustawić tylko raz dla wątku.  
  
 Jeśli stan apartamentu nie zostanie ustawiony przed uruchomieniem wątku, wątek zostanie zainicjowany jako Apartament wielowątkowy (MTA). Wątek finalizatora i wszystkie wątki kontrolowane przez <xref:System.Threading.ThreadPool> są MTA.  
  
> [!IMPORTANT]
> W przypadku kodu uruchamiania aplikacji jedynym sposobem sterowania stanem apartamentu jest zastosowanie <xref:System.MTAThreadAttribute> procedury <xref:System.STAThreadAttribute> lub do punktu wejścia. W .NET Framework 1,0 i 1,1 <xref:System.Threading.Thread.ApartmentState%2A> Właściwość można ustawić jako pierwszy wiersz kodu. Nie jest to dozwolone w .NET Framework 2,0.  
  
 Zarządzane obiekty, które są widoczne dla modelu COM, zachowują się tak, jakby były zagregowane organizatora wolnych wątków. Innymi słowy, mogą one być wywoływane z dowolnego apartamentu COM w sposób wolny od wątków. Jedynymi obiektami zarządzanymi, które nie wykazują tego zachowania, są te obiekty, które pochodzą z <xref:System.EnterpriseServices.ServicedComponent> lub <xref:System.Runtime.InteropServices.StandardOleMarshalObject>.  
  
 W zarządzanym świecie nie ma żadnego wsparcia <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> , chyba że używasz kontekstów ani wystąpień zarządzanych powiązanych z kontekstem. W przypadku korzystania z usług przedsiębiorstwa, obiekt musi pochodzić od <xref:System.EnterpriseServices.ServicedComponent> (, który jest samym <xref:System.ContextBoundObject>pochodną).  
  
 Gdy kod zarządzany jest wywoływany z obiektami COM, zawsze jest zgodny z regułami COM. Innymi słowy, wywoływany przez serwery proxy Apartment COM i otoki kontekstu COM+ 1,0, zgodnie z ustawieniami OLE32.  
  
## <a name="blocking-issues"></a>Problemy z blokowaniem  

Jeśli wątek wywołuje niezarządzane wywołanie do systemu operacyjnego, który zablokował wątek w kodzie niezarządzanym, środowisko uruchomieniowe nie przejmie kontroli nad <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> lub <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. W przypadku <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, środowisko uruchomieniowe oznacza wątek do przerwania i przejmuje kontrolę nad nim po ponownym wprowadzeniu kodu zarządzanego. Zalecane jest używanie blokowania zarządzanego zamiast blokowania niezarządzanego. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> ,<xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> ,,<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>,, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> , i tak dalej, odpowiada i do. <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> Ponadto jeśli wątek znajduje się w Apartment jednowątkowym, wszystkie te zarządzane operacje blokowania będą prawidłowo przekazywać komunikaty w Twojej organizacji, gdy wątek zostanie zablokowany.  

## <a name="threads-and-fibers"></a>Wątki i włókien

Model wątkowości .NET nie obsługuje [włókien](/windows/desktop/procthread/fibers). Nie należy wywoływać żadnej funkcji niezarządzanej, która jest implementowana przy użyciu włókien. Takie wywołania mogą spowodować awarię środowiska uruchomieniowego .NET.

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>
- <xref:System.Threading.ThreadState>
- <xref:System.EnterpriseServices.ServicedComponent>
- <xref:System.Threading.Thread>
- <xref:System.Threading.Monitor>
