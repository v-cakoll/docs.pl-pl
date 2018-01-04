---
title: "Instrukcje: Hostowanie usługi przepływu pracy przy użyciu rozwiązania AppFabric w systemie Windows Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc7af813f7fff422a2513c58c9e3cba6376de060
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>Instrukcje: Hostowanie usługi przepływu pracy przy użyciu rozwiązania AppFabric w systemie Windows Server
Hostowanie usług przepływu pracy w aplikacji sieci szkieletowej jest podobny do hostingu w środowisku usług IIS / WAS. Jedyna różnica polega na te narzędzia, które zapewnia AppFabric wdrażania, monitorowania i zarządzania usług przepływu pracy. W tym temacie korzysta z usługi przepływu pracy utworzone w [Tworzenie usługi przepływu pracy długotrwałe](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md). Ten temat przeprowadzi Cię przez proces tworzenia usługi przepływu pracy. W tym temacie objaśnia sposób hosta usługi przepływu pracy przy użyciu aplikacji sieci szkieletowej. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Windows Server AppFabric, zobacz [dokumentacją sieci szkieletowej systemu Windows Server aplikacji](http://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409). Przed wykonaniem poniższych instrukcji upewnij się, że masz systemu Windows Server AppFabric zainstalowane.  Aby zrobić to open zapasowej Internetowe usługi informacyjne (inetmgr.exe), kliknij nazwę serwera w **połączeń** wyświetlić, kliknij przycisk witryny, a następnie kliknij przycisk **domyślna witryna sieci Web**. W prawej części ekranu powinna być widoczna sekcja o nazwie **AppFabric**. Jeśli nie widzisz tej sekcji (będzie górnej części okienka po prawej stronie) nie masz AppFabric zainstalowane. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Instalowanie systemu Windows Server AppFabric zobacz [Instalowanie systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193136).  
  
### <a name="creating-a-simple-workflow-service"></a>Tworzenie usługi Simple przepływu pracy  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] i załadowania rozwiązania OrderProcessing utworzony w [Tworzenie usługi przepływu pracy długotrwałe](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md) tematu.  
  
2.  Kliknij prawym przyciskiem myszy **OrderService** projekt i wybierz **właściwości** i wybierz **Web** kartę.  
  
3.  W **Akcja uruchamiania** strony właściwości zaznacz **określonej strony** i wpisz Service1.xamlx w polu edycji.  
  
4.  W **serwerów** strony właściwości zaznacz **użycia lokalnego serwera sieci Web usług IIS** i wprowadź następujący adres URL: `http://localhost/OrderService`.  
  
5.  Kliknij przycisk **utworzyć katalog wirtualny** przycisku. Spowoduje to utworzenie nowego katalogu wirtualnego i konfigurowanie projektu Aby skopiować pliki potrzebne do katalogu wirtualnego, podczas tworzenia projektu.  Alternatywnie można ręcznie skopiować .xamlx pliku web.config i wszystkie wymagane biblioteki dll do katalogu wirtualnego.  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>Konfigurowanie usługi przepływu pracy w systemu Windows Server AppFabric  
  
1.  Otwórz Menedżera internetowych usług informacyjnych (inetmgr.exe).  
  
2.  Przejdź do katalogu wirtualnego OrderService w **połączeń** okienka.  
  
3.  OrderService kliknij prawym przyciskiem myszy i wybierz **Zarządzanie WCF i WF usług**, **Konfiguruj...** . **Konfigurowanie usługi WCF i WF dla aplikacji** zostanie wyświetlone okno dialogowe.  
  
4.  Wybierz **ogólne** kartę, aby wyświetlić ogólne informacje o aplikacji, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Na karcie Ogólne okna dialogowego konfiguracji sieci szkieletowej aplikacji](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-general.gif "AppFabricConfiguration — ogólne")  
  
5.  Wybierz **monitorowanie** kartę. Zawiera różne ustawienia monitorowania, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Karta sieci szkieletowej konfiguracji monitorowania aplikacji](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration monitorowania")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Konfigurowanie monitorowania usługi przepływu pracy w aplikacji sieci szkieletowej zobacz [konfigurowania monitorowania przy użyciu rozwiązania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193153).  
  
6.  Wybierz **utrwalania przepływu pracy** kartę. Dzięki temu można skonfigurować aplikację do używania dostawcy trwałości domyślnej aplikacji sieci szkieletowej jak pokazano na poniższym zrzucie ekranu.  
  
     ![Konfiguracja aplikacji sieci szkieletowej &#45; Trwałość](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-persistence.gif "AppFabricConfiguration trwałości")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Konfigurowanie trwałości przepływu pracy w systemu Windows Server AppFabric zobacz [Konfigurowanie trwałości przepływu pracy w aplikacji sieci szkieletowej](http://go.microsoft.com/fwlink/?LinkId=193148).  
  
7.  Wybierz **przepływu pracy zarządzania hostem** kartę. Dzięki temu można określić, kiedy bezczynne wystąpienia przepływu pracy usługi powinny być zwolnione i utrwalone, jak pokazano na poniższym zrzucie ekranu.  
  
     ![AppFabric w konfiguracji przepływu pracy hosta zarządzania](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-management.gif "AppFabricConfiguration zarządzania")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Zobacz konfiguracji zarządzania hosta przepływu pracy [Konfigurowanie zarządzania hosta przepływu pracy w aplikacji sieci szkieletowej](http://go.microsoft.com/fwlink/?LinkId=193151).  
  
8.  Wybierz **Auto-Start** kartę. Dzięki temu można określić ustawienia automatycznego uruchamiania usługi przepływu pracy w aplikacji, jak pokazano na poniższym zrzucie ekranu.  
  
     ![&#45;aplikacji sieci szkieletowej automatycznie; Konfiguracja uruchamiania](../../../../docs/framework/wcf/feature-details/media/appfabricconfigurationautostart.gif "AppFabricConfigurationAutostart")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Konfigurowanie automatycznego uruchamiania zobacz [Konfigurowanie automatycznego uruchamiania przy użyciu rozwiązania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193150).  
  
9. Wybierz **ograniczania** kartę. Dzięki temu można skonfigurować ustawienia ograniczenia przepustowości usługi przepływu pracy, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Ograniczanie konfiguracji aplikacji sieci szkieletowej](../../../../docs/framework/wcf/feature-details/media/appfabricconfigurationthrottling.gif "AppFabricConfigurationThrottling")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Konfigurowanie ograniczania zobacz [Konfigurowanie ograniczania przy użyciu rozwiązania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193149).  
  
10. Wybierz **zabezpieczeń** kartę. Dzięki temu można skonfigurować ustawień zabezpieczeń dla aplikacji, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Konfiguracja zabezpieczeń aplikacji sieci szkieletowej](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-security.gif "AppFabricConfiguration zabezpieczeń")  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Konfigurowanie zabezpieczeń przy użyciu systemu Windows Server AppFabric zobacz [Konfigurowanie zabezpieczeń przy użyciu rozwiązania AppFabric](http://go.microsoft.com/fwlink/?LinkId=193152).  
  
### <a name="using-windows-server-app-fabric"></a>Przy użyciu systemu Windows Server AppFabric  
  
1.  Skompiluj rozwiązanie, które można skopiować pliki niezbędne do katalogu wirtualnego.  
  
2.  Kliknij prawym przyciskiem myszy projekt OrderClient i wybierz **debugowania**, **uruchomić nowe wystąpienie** można uruchomić aplikacji klienckiej.  
  
3.  Klient zostanie wykonane, a program Visual Studio spowoduje wyświetlenie **dołączyć ostrzeżenie o zabezpieczeniach** okno dialogowe, kliknij przycisk **nie dołączyć** przycisku. Ta wartość informuje Visual Studio, aby nie dołączyć do procesu programu IIS do debugowania.  
  
4.  Aplikacja kliencka będzie natychmiast wywołania usługi przepływu pracy, a następnie poczekaj. Usługa przepływ pracy zostanie umieszczona w stanie bezczynności i utrwalone. Można to sprawdzić, uruchamianie Internetowe usługi informacyjne (inetmgr.exe), przechodząc do OrderService w okienku połączenia i wybranie go. Następnie kliknij ikonę pulpitu nawigacyjnego aplikacji sieci szkieletowej w okienku po prawej stronie. W obszarze utrwalone wystąpień WF pojawi się, że istnieje jedno wystąpienie usługi utrwalonych przepływów pracy, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Pulpit nawigacyjny aplikacji sieci szkieletowej](../../../../docs/framework/wcf/feature-details/media/appfabricdashboard.gif "AppFabricDashboard")  
  
     **Historii wystąpienia WF** Wyświetla informacje na temat usługi przepływu pracy, takich jak liczbę aktywacji usługi przepływu pracy, liczbę zakończeń wystąpienia usługi przepływu pracy i liczba wystąpień przepływów pracy z błędami. W obszarze wystąpienia aktywności lub bezczynności, które zostanie wyświetlony link klikając łącze wyświetli więcej informacji na temat wystąpień bezczynności przepływu pracy, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Szczegóły wystąpienia przepływu pracy utrwalone](../../../../docs/framework/wcf/feature-details/media/persisteddetail.gif "PersistedDetail")  
  
     Aby uzyskać więcej informacji na temat systemu Windows Server AppFabric funkcje i sposobu ich używania, zobacz [Hosting funkcje systemu Windows Server aplikacji sieci szkieletowej](http://go.microsoft.com/fwlink/?LinkID=193143&clcid=0x409)  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie długo działającej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=193143)  
 [Instalowanie systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193136)  
 [Dokumentację systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409)
