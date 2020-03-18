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
ms.openlocfilehash: 6ab0cc7c1ec2f7bbc633ac966dd18ab3ea7a395b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127541"
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Zarządzane i niezarządzane wątki w systemie Windows

Zarządzanie wszystkimi wątkami odbywa <xref:System.Threading.Thread> się za pośrednictwem klasy, w tym wątków utworzonych przez środowisko uruchomieniowe języka wspólnego i tych utworzonych poza środowiskiem uruchomieniowym, które wchodzą do środowiska zarządzanego w celu wykonania kodu. Środowisko wykonawcze monitoruje wszystkie wątki w procesie, które kiedykolwiek wykonały kod w środowisku zarządzanego wykonywania. Nie śledzi żadnych innych wątków. Wątki mogą wejść do środowiska wykonawczego zarządzanego za pośrednictwem współdziałania COM (ponieważ środowisko wykonawcze udostępnia obiekty zarządzane jako obiekty COM do świata niezarządzanego), funkcji [COM DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject) i wywołania platformy.  
  
 Gdy wątek niezarządzany wchodzi do czasu wykonywania za pośrednictwem, na przykład otoki wywoływanej COM, system sprawdza <xref:System.Threading.Thread> magazyn lokalny dla wątków tego wątku w celu wyszukania wewnętrznego obiektu zarządzanego. Jeśli zostanie znaleziony, czas wykonywania jest już świadomy tego wątku. Jeśli jednak nie można go znaleźć, program <xref:System.Threading.Thread> runtime tworzy nowy obiekt i instaluje go w magazynie lokalnym wątku tego wątku.  
  
 W zarządzanym <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> wątkowaniu jest stabilna identyfikacja wątku zarządzanego. Przez cały okres istnienia wątku nie będzie kolidować z wartością z innego wątku, niezależnie od domeny aplikacji, z której można uzyskać tę wartość.  
  
> [!NOTE]
> Identyfikator **ThreadId** systemu operacyjnego nie ma stałej relacji z zarządzanym wątkiem, ponieważ host niezarządzany może kontrolować relację między wątkami zarządzanymi i niezarządzanymi. W szczególności zaawansowany host może używać interfejsu API fiber do planowania wielu zarządzanych wątków względem tego samego wątku systemu operacyjnego lub przenoszenia zarządzanego wątku między różnymi wątkami systemu operacyjnego.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Mapowanie z wątków Win32 do wątków zarządzanych

 W poniższej tabeli mapy Win32 wątków elementów do ich przybliżonego odpowiednika wykonywania. Należy zauważyć, że to mapowanie nie reprezentuje identyczne funkcje. Na przykład **TerminateThread** nie wykonuje **finally** klauzule lub zwolnić zasoby i nie można zapobiec. Jednak <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wykonuje cały kod wycofywania, odzyskuje wszystkie zasoby i <xref:System.Threading.Thread.ResetAbort%2A>można odmówić przy użyciu . Pamiętaj, aby uważnie przeczytać dokumentację przed dokonaniem założeń dotyczących funkcjonalności.  
  
|w Win32|W czasie wykonywania języka wspólnego|  
|--------------|------------------------------------|  
|**Createthread**|Połączenie **nici** i<xref:System.Threading.ThreadStart>|  
|**TerminateThread (Zakończone wątkiem)**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**SuspendThread (Wstrzymaj wątek)**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**ResumeThread (ResumeThread)**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**Snu**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|**WaitForSingleObject** w dojściu wątku|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**Exitthread**|Brak odpowiednika|  
|**GetCurrentThread (Wątek getcurrent)**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**Ustaw priorytet wątku**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Brak odpowiednika|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Brak odpowiednika|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|Blisko **CoInitializeEx** (OLE32. DLL)|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Zarządzane wątki i apartamenty COM

Zarządzany wątek można oznaczyć, aby wskazać, że będzie gospodarzem mieszkania [jednowątkowego](/windows/desktop/com/single-threaded-apartments) lub [wielowątkowego.](/windows/desktop/com/multithreaded-apartments) (Aby uzyskać więcej informacji na temat architektury wątków COM, zobacz [Procesy, wątki i apartamenty](/windows/desktop/com/processes--threads--and-apartments).) , <xref:System.Threading.Thread.GetApartmentState%2A> <xref:System.Threading.Thread.SetApartmentState%2A>i <xref:System.Threading.Thread.TrySetApartmentState%2A> metody <xref:System.Threading.Thread> klasy zwracają i przypisują stan mieszkania wątku. Jeśli stan nie został <xref:System.Threading.Thread.GetApartmentState%2A> ustawiony, zwraca . <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>  
  
 Właściwość można ustawić tylko wtedy, gdy <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> wątek jest w stanie; można go ustawić tylko raz dla wątku.  
  
 Jeśli stan mieszkania nie jest ustawiony przed rozpoczęciem wątku, wątek jest inicjowany jako apartament wielowątkowy (MTA). Wątek finalizatora i wszystkie <xref:System.Threading.ThreadPool> wątki kontrolowane przez są MTA.  
  
> [!IMPORTANT]
> W przypadku kodu uruchamiania aplikacji jedynym sposobem kontrolowania stanu mieszkania jest zastosowanie procedury punktu wejścia <xref:System.MTAThreadAttribute> lub <xref:System.STAThreadAttribute> do procedury punktu wejścia. W .NET Framework 1.0 i 1.1 <xref:System.Threading.Thread.ApartmentState%2A> właściwość może być ustawiona jako pierwszy wiersz kodu. Nie jest to dozwolone w .NET Framework 2.0.  
  
 Zarządzane obiekty, które są udostępniane com zachowują się tak, jakby zagregowane free-threaded organizatora. Innymi słowy, można je wywołać z dowolnego mieszkania COM w sposób swobodny. Jedynymi obiektami zarządzanymi, które nie wykazują tego zachowania bez <xref:System.EnterpriseServices.ServicedComponent> <xref:System.Runtime.InteropServices.StandardOleMarshalObject>wątków, są te obiekty, które pochodzą z lub .  
  
 W zarządzanym świecie nie ma <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> żadnej obsługi dla, chyba że używasz kontekstów i wystąpień zarządzanych kontekstowych. Jeśli używasz Usługi Enterprise Services, obiekt musi <xref:System.EnterpriseServices.ServicedComponent> pochodzić od (który sam pochodzi od <xref:System.ContextBoundObject>).  
  
 Gdy kod zarządzany wywołuje com obiektów, zawsze jest zgodna z regułami COM. Innymi słowy wywołuje za pośrednictwem com apartament proxy i COM + 1.0 otoki kontekstu podyktowane przez OLE32.  
  
## <a name="blocking-issues"></a>Problemy z blokowaniem  

Jeśli wątek wykonuje niezarządzane wywołanie do systemu operacyjnego, który zablokował wątek w kodzie niezarządzanym, czas wykonywania nie przejmie nad nim kontroli dla <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> lub <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. W przypadku <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, czas wykonywania oznacza wątek **abort** i przejmuje kontrolę nad nim, gdy ponownie wprowadza kod zarządzany. Zaleca się korzystanie z blokowania zarządzanego, a nie blokowania niezarządzanego. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>, , i tak <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> dalej <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>są dostosowane do i do . Ponadto, jeśli wątek znajduje się w mieszkaniu jednowątkowym, wszystkie te zarządzane operacje blokowania poprawnie pompują wiadomości w twoim mieszkaniu, gdy wątek jest zablokowany.  

## <a name="threads-and-fibers"></a>Nici i włókna

Model wątkowości .NET nie obsługuje [włókien](/windows/desktop/procthread/fibers). Nie należy wywoływać do żadnej funkcji niezarządzanej, który jest implementowany przy użyciu włókien. Takie wywołania mogą spowodować awarię programu .NET w czasie wykonywania.

## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>
- <xref:System.Threading.ThreadState>
- <xref:System.EnterpriseServices.ServicedComponent>
- <xref:System.Threading.Thread>
- <xref:System.Threading.Monitor>
