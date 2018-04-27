---
title: Zarządzana i niezarządzana wątkowość w systemie Windows
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], unmanaged
- threading [.NET Framework], managed
- managed threading
ms.assetid: 4fb6452f-c071-420d-9e71-da16dee7a1eb
caps.latest.revision: 17
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 66bf8458a3f4f9dd622129e82acb659dddf8467a
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="managed-and-unmanaged-threading-in-windows"></a>Zarządzana i niezarządzana wątkowość w systemie Windows
Zarządzanie wszystkie wątki odbywa się za pośrednictwem <xref:System.Threading.Thread> klasy, w tym utworzone przez środowisko uruchomieniowe języka wspólnego wątki i utworzone poza środowisko uruchomieniowe, które wprowadź zarządzanego środowiska do wykonywania kodu. Środowisko uruchomieniowe monitoruje wszystkie wątki w procesie, które kiedykolwiek wykonali kodu w ramach zarządzanego środowiska wykonawczego. Nie śledzi inne wątki. Wątki można wprowadzić zarządzanego środowiska wykonawczego za pomocą modelu COM interop (ponieważ środowisko uruchomieniowe przedstawia zarządzanych obiektów w postaci obiektów COM niezarządzane world), modelu COM [metody DllGetClassObject](https://msdn.microsoft.com/library/ms680760.aspx) funkcji i wywołanie platformy.  
  
 Gdy niezarządzany wątek pojawia się za pośrednictwem środowiska uruchomieniowego, na przykład wywoływana otoka COM, system sprawdza magazynu wątków lokalnych wątek do wyszukiwania dla wewnętrznego zarządzanych <xref:System.Threading.Thread> obiektu. Jeśli został znaleziony, środowisko wykonawcze jest już świadomość tego wątku. Nie można znaleźć jednego, jednak środowiska uruchomieniowego tworzy nową <xref:System.Threading.Thread> obiektu i instaluje je w magazynie lokalnej wątku tego wątku.  
  
 W zarządzanych wątków, <xref:System.Threading.Thread.GetHashCode%2A?displayProperty=nameWithType> jest identyfikacja stabilna zarządzanego wątku. Przez czas ich istnienia z wątku zostanie on nie kolidują z wartości z innego wątku, niezależnie od domeny aplikacji, z którego można pobierać tę wartość.  
  
> [!NOTE]
>  System operacyjny **ThreadId** nie ma stałej relacji do zarządzanego wątku, ponieważ niezarządzane hosta można kontrolować relacji między wątkami zarządzane i niezarządzane. W szczególności zaawansowane hosta można użyć interfejsu API Fiber można zaplanować wiele wątków zarządzanych względem tego samego wątku systemu operacyjnego lub zarządzanego wątku między wątki innego systemu operacyjnego.  
  
## <a name="mapping-from-win32-threading-to-managed-threading"></a>Mapowanie z Win32 wątków do zarządzanego wątkowość  
 Poniższa tabela mapuje Win32 wątkowości elementy do ich przybliżonej środowiska wykonawczego równoważne. Należy pamiętać, że to mapowanie nie reprezentuje identyczną funkcjonalność. Na przykład **funkcji TerminateThread** nie wykonuj **koniec** klauzule lub zwolnić zasoby, a nie można zapobiec. Jednak <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wykonuje kod wycofywania, zwraca wszystkie zasoby i może nastąpić odmowa przy użyciu <xref:System.Threading.Thread.ResetAbort%2A>. Należy zapoznać się z dokumentacją ściśle, przed wprowadzeniem założenia dotyczące funkcji.  
  
|W systemie Win32|W środowisko uruchomieniowe języka wspólnego|  
|--------------|------------------------------------|  
|**CreateThread**|Kombinacja **wątku** i <xref:System.Threading.ThreadStart>|  
|**Funkcji TerminateThread**|<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>|  
|**SuspendThread**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>|  
|**ResumeThread**|<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>|  
|**uśpienia**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>|  
|**WaitForSingleObject** na dojście wątku|<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>|  
|**ExitThread**|Odpowiednika|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=nameWithType>|  
|**Wykonanie funkcji SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>|  
|Odpowiednika|<xref:System.Threading.Thread.Name%2A?displayProperty=nameWithType>|  
|Odpowiednika|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>|  
|Zamknij, aby **funkcja CoInitializeEx** (OLE32. BIBLIOTEKI DLL)|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>|  
  
## <a name="managed-threads-and-com-apartments"></a>Zarządzane wątki i Apartamentach COM  
 Może być oznaczony zarządzanych wątków, aby wskazać, który będzie obsługiwał [jednowątkowe](https://msdn.microsoft.com/library/windows/desktop/ms680112.aspx) lub [wielowątkowe](https://msdn.microsoft.com/library/windows/desktop/ms693421.aspx) apartamentu. (Aby uzyskać więcej informacji na temat modelu COM wątkowość architektury, zobacz [procesy, wątki i Apartamentach](https://msdn.microsoft.com/library/windows/desktop/ms693344.aspx).) <xref:System.Threading.Thread.GetApartmentState%2A>, <xref:System.Threading.Thread.SetApartmentState%2A>, I <xref:System.Threading.Thread.TrySetApartmentState%2A> metody <xref:System.Threading.Thread> klasy powrotu i przypisz stanu apartamentu wątku. Jeśli nie ustawiono stan, <xref:System.Threading.Thread.GetApartmentState%2A> zwraca <xref:System.Threading.ApartmentState.Unknown?displayProperty=nameWithType>.  
  
 Właściwość można ustawić tylko wtedy, gdy wątek znajduje się w <xref:System.Threading.ThreadState.Unstarted?displayProperty=nameWithType> stanu; można go ustawić tylko raz dla wątku.  
  
 Jeśli stanu apartamentu nie jest ustawiona przed uruchomieniem wątku, wątek został zainicjowany jako wielowątkowe apartamentu (MTA). Wątku finalizatora i wszystkie wątki kontrolowane przez <xref:System.Threading.ThreadPool> są MTA.  
  
> [!IMPORTANT]
>  Dla kodu uruchomienia aplikacji, jedynym sposobem, aby kontrolować stan apartamentu stosuje się <xref:System.MTAThreadAttribute> lub <xref:System.STAThreadAttribute> się z wpisem punktu procedury. .NET Framework 1.0 i 1.1 <xref:System.Threading.Thread.ApartmentState%2A> właściwość można ustawić jako pierwszy wiersz kodu. Jest to niedozwolone w .NET Framework 2.0.  
  
 Zarządzane obiekty, które są widoczne dla modelu COM zachowują się tak, jakby ich miał agregować bezwątkowy organizatora. Innymi słowy ich może zostać wywołana z dowolnego apartamentu COM w sposób bezwątkowy. Te obiekty, które pochodzą z są tylko obiektów zarządzanych, które nie wykazują to zachowanie bezwątkowe <xref:System.EnterpriseServices.ServicedComponent> lub <xref:System.Runtime.InteropServices.StandardOleMarshalObject>.  
  
 W kodzie zarządzanym nie jest obsługiwane dla <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> tylko w przypadku konteksty i zarządzanych wystąpień związane z kontekstem. Jeśli używasz usług dla przedsiębiorstw, a następnie obiekt musi pochodzić od <xref:System.EnterpriseServices.ServicedComponent> (który sam pochodzi od <xref:System.ContextBoundObject>).  
  
 Kod zarządzany uwidacznia do obiektów COM, będzie zawsze wykonywać reguły COM. Innymi słowy połączenia za pośrednictwem serwerów proxy apartamentu COM i otoki kontekstu modelu COM + 1.0, zgodnie z ustawieniem OLE32.  
  
## <a name="blocking-issues"></a>Problemy z blokowaniem  
 Jeśli wątek powoduje wywołanie niezarządzanych do systemu operacyjnego, który został zablokowany wątku za pomocą kodu niezarządzanego, środowisko uruchomieniowe nie będzie przejąć kontrolę nad dla <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> lub <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. W przypadku programu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, środowisko uruchomieniowe oznacza wątku dla **przerwać** i przejmuje kontrolę nad go podczas ponownego wprowadza kodu zarządzanego. Zaleca się przy użyciu zarządzanego blokuje zamiast blokuje niezarządzane. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>,<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>, <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>i tak dalej są wszystkie odbierać <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Ponadto jeśli Twoje wątku jednowątkowego apartamentu, tych zarządzanej operacji blokowania zostanie poprawnie pompa wiadomości w Twojej apartamentu podczas Twojej wątek jest zablokowany.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType>  
 <xref:System.Threading.ThreadState>  
 <xref:System.EnterpriseServices.ServicedComponent>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.Monitor>
