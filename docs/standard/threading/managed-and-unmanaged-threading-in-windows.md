---
title: Zarządzana i niezarządzana wątkowość w systemie Windows
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], unmanaged
- threading [.NET Framework], managed
- managed threading
ms.assetid: 4fb6452f-c071-420d-9e71-da16dee7a1eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1be82fd9f26e382f20913551f67e8303cf20e03b
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257321"
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Zarządzana i niezarządzana wątkowość w systemie Windows
Zarządzanie wszystkie wątki odbywa się za pośrednictwem <xref:System.Threading.Thread> klasy, w tym wątków utworzone przez środowisko uruchomieniowe języka wspólnego, a utworzone poza środowisko uruchomieniowe, które należy wprowadzić zarządzane środowisko do wykonywania kodu. Środowisko uruchomieniowe monitoruje wszystkie wątki w swoim procesie, które kiedykolwiek wykonali kod w zarządzanym środowisku wykonywania. Żądania nie Śledź innych wątków. Wątki, które można wprowadzić zarządzanym środowisku wykonywania za pomocą COM interop (ponieważ środowisko uruchomieniowe uwidacznia zarządzane obiekty jako obiekty COM do niezarządzanego świata), COM [DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject) funkcji i wywołanie platformy.  
  
 Gdy wątek niezarządzany wejdzie w czasie wykonywania za pomocą, na przykład wywołalne opakowanie COM, system sprawdza magazynu wątków lokalnych wątek do wyszukiwania dla zarządzanych przy użyciu wewnętrznego <xref:System.Threading.Thread> obiektu. Jeśli został znaleziony, środowisko wykonawcze jest już pamiętać o tym wątku. Nie można znaleźć jednego, jednak środowisko uruchomieniowe tworzy nową <xref:System.Threading.Thread> obiektu i instaluje je w magazynie wątków lokalnych w tym wątku.  
  
 W zarządzanych wątków, <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> jest identyfikacja stabilne wątków zarządzanych. Okres istnienia wątek będzie go nie kolidują z wartości z innego wątku, niezależnie od tego, w domenie aplikacji, z którego można uzyskać tę wartość.  
  
> [!NOTE]
>  System operacyjny **ThreadId** nie ma stałej relacji wątków zarządzanych, ponieważ niezarządzany host może kontrolować relacji między wątkami zarządzanych i niezarządzanych. W szczególności zaawansowanych hosta można użyć interfejsu API Fiber zaplanować wiele wątków zarządzanych względem tego samego wątku systemu operacyjnego lub Przenieś wątek między wątkami innego systemu operacyjnego.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Mapowanie z Win32 wątków do zarządzanych wątkach  
 Poniższa tabela zawiera mapowanie elementów wątkowości Win32 do ich przybliżony środowiska uruchomieniowego równoważne. Należy pamiętać, że to mapowanie nie reprezentuje identyczną funkcjonalność. Na przykład **TerminateThread** nie jest wykonywane **na koniec** klauzule lub Zwolnij część zasobów i nie można zapobiec. Jednak <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wykonuje kod wycofywania, odzyskuje wszystkie zasoby i może nastąpić odmowa przy użyciu <xref:System.Threading.Thread.ResetAbort%2A>. Należy zapoznać się z dokumentacją ściśle przed wprowadzania założeń dotyczących funkcji.  
  
|W systemie Win32|W środowisku uruchomieniowym języka|  
|--------------|------------------------------------|  
|**CreateThread**|Kombinacja **wątku** i <xref:System.Threading.ThreadStart>|  
|**TerminateThread**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**SuspendThread**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**ResumeThread**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**Stan uśpienia**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|**WaitForSingleObject** na dojście wątku|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**ExitThread**|Odpowiednika|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Odpowiednika|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Odpowiednika|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|Zamknij, aby **CoInitializeEx** (OLE32. BIBLIOTEKA DLL)|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Zarządzanych wątkami i Apartamentach COM  
 Wątków zarządzanych mogą zostać oznaczone jako, aby wskazać, że będzie obsługiwać [apartamentem](/windows/desktop/com/single-threaded-apartments) lub [wielowątkowe](/windows/desktop/com/multithreaded-apartments) typu apartment. (Aby uzyskać więcej informacji na temat COM wątkowości architektury, zobacz [procesy, wątki i Apartamentach](https://msdn.microsoft.com/library/windows/desktop/ms693344.aspx).) <xref:System.Threading.Thread.GetApartmentState%2A>, <xref:System.Threading.Thread.SetApartmentState%2A>, I <xref:System.Threading.Thread.TrySetApartmentState%2A> metody <xref:System.Threading.Thread> klasy return i przypisz stan apartamentu wątku. Jeśli nie ustawiono stan <xref:System.Threading.Thread.GetApartmentState%2A> zwraca <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>.  
  
 Właściwość można ustawić tylko wtedy, gdy znajduje się wątek <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> stanu; można ustawić tylko raz dla wątku.  
  
 Jeśli nie ustawiono stan apartamentu, przed rozpoczęciem wątek, wątek jest inicjowany jako wielowątkowe apartamentu (MTA). Wątek finalizatora oraz gdy wszystkie wątki w wartości clientauthtrustmode <xref:System.Threading.ThreadPool> są MTA.  
  
> [!IMPORTANT]
>  Dla kodu uruchamiania aplikacji, jedynym sposobem, aby kontrolować stan apartamentu stosuje się <xref:System.MTAThreadAttribute> lub <xref:System.STAThreadAttribute> do wpisu punktu procedury. W .NET Framework 1.0 i 1.1 <xref:System.Threading.Thread.ApartmentState%2A> właściwość można ustawić jako pierwszy wiersz kodu. Jest to niedozwolone w programie .NET Framework 2.0.  
  
 Zarządzane obiekty, które są widoczne dla modelu COM zachowują się tak, jakby były one zagregowane bezwątkowego. Innymi słowy ich można wywołać z dowolnego apartamentu COM w sposób bezwątkowy. Tylko obiekty zarządzane, które nie wykazują to zachowanie bezwątkowy są te obiekty, które wynikają z <xref:System.EnterpriseServices.ServicedComponent> lub <xref:System.Runtime.InteropServices.StandardOleMarshalObject>.  
  
 W kodzie zarządzanym, nie jest obsługiwane dla <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> chyba że używany jest kontekst i związane z kontekstem wystąpienia zarządzanego. Jeśli używasz usług dla przedsiębiorstw, a następnie obiekt musi pochodzić od klasy <xref:System.EnterpriseServices.ServicedComponent> (który sam pochodzi od <xref:System.ContextBoundObject>).  
  
 Wywołuje kodu zarządzanego do obiektów COM, jest zawsze zgodna COM reguły. Innymi słowy połączenia za pośrednictwem serwerów proxy apartamentu COM i otoki kontekstu COM + 1.0, zgodnie z ustawieniem OLE32.  
  
## <a name="blocking-issues"></a>Problemy z blokowaniem  
 Jeśli wątek sprawia, że wywołanie niezarządzanych w systemie operacyjnym, który został zablokowany wątek w niezarządzanym kodzie, środowisko wykonawcze nie podejmie kontrolę nad nim dla <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> lub <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. W przypadku właściwości <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, środowisko uruchomieniowe oznacza wątku dla **przerwać** i ma kontrolę nad nim, gdy wejdzie ona ponownie kodu zarządzanego. Zaleca się, można ich używać blokowania zarządzanych zamiast blokowania niezarządzanych. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>, <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>i tak dalej wszystkie reagują na <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Ponadto jeśli wątek jest jednowątkowym apartamentem, tych zarządzanych operacji blokowania będzie poprawnie pompy komunikatów w Twojego mieszkania podczas, gdy wątek jest zablokowany.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>  
 <xref:System.Threading.ThreadState>  
 <xref:System.EnterpriseServices.ServicedComponent>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.Monitor>
