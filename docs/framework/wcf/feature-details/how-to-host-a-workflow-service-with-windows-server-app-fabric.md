---
title: 'Instrukcje: hostowanie usługi przepływu pracy przy użyciu rozwiązania AppFabric w systemie Windows Server'
ms.date: 03/30/2017
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
ms.openlocfilehash: d1042aca7e4127c39e59bf0bf400974f0cecb1e8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314740"
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>Instrukcje: hostowanie usługi przepływu pracy przy użyciu rozwiązania AppFabric w systemie Windows Server
Hostowanie usług przepływu pracy w sieci szkieletowej aplikacji jest podobny do hostowania w usługach IIS / WAS. Jedyna różnica polega na narzędzia, których App Fabric umożliwia wdrażanie, monitorowanie i zarządzanie usług przepływu pracy. Ten temat używa usługi przepływu pracy utworzone w [tworzenie długo działającej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md). Ten temat przeprowadzi Cię Tworzenie usługi przepływu pracy. W tym temacie wyjaśniono, jak hostowanie usługi przepływu pracy przy użyciu App Fabric. Aby uzyskać więcej informacji na temat AppFabric w systemie Windows Server, zobacz [dodatku App Fabric dokumentację dla systemu Windows Server](https://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409). Przed wykonaniem poniższych kroków upewnij się, że masz systemu Windows Server AppFabric zainstalowane.  Aby zrobić to open się Internet Information Services (inetmgr.exe), kliknij nazwę serwera w **połączeń** wyświetlić, kliknij pozycję witryny, a następnie kliknij przycisk **domyślna witryna sieci Web**. W prawym rogu ekranu, powinien zostać wyświetlony sekcję o nazwie **App Fabric**. Jeśli nie widzisz tej sekcji (będą mieć wartość górnej części okienka po prawej stronie) nie masz App Fabric zainstalowane. Aby uzyskać więcej informacji na temat instalowania systemu Windows Server AppFabric zobacz [instalacji systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=193136).  
  
### <a name="creating-a-simple-workflow-service"></a>Tworzenie usługi prostego przepływu pracy  
  
1. Otwórz program Visual Studio 2012 i obciążenia należy utworzyć rozwiązanie OrderProcessing [tworzenie długo działającej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md) tematu.  
  
2. Kliknij prawym przyciskiem myszy **OrderService** projektu, a następnie wybierz **właściwości** i wybierz **Web** kartę.  
  
3. W **Akcja uruchamiania** sekcji na stronie właściwości wybierz **konkretnej strony** i wpisz Service1.xamlx w polu edycji.  
  
4. W **serwerów** sekcji na stronie właściwości wybierz **użycia lokalnego serwera sieci Web usług IIS** i wpisz następujący adres URL: `http://localhost/OrderService`.  
  
5. Kliknij przycisk **Utwórz katalog wirtualny** przycisku. Spowoduje to utworzenie nowego katalogu wirtualnego i skonfigurowanie projektu, aby skopiować pliki potrzebne do katalogu wirtualnego, podczas kompilowania projektu.  Alternatywnie możesz można ręcznie skopiować .xamlx pliku web.config i wszelkich wymaganych bibliotek DLL do katalogu wirtualnego.  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>Konfigurowanie przepływu pracy usługi hostowanej w systemie Windows Server AppFabric  
  
1. Otwórz Menedżera internetowych usług informacyjnych (inetmgr.exe).  
  
2. Przejdź do katalogu wirtualnego OrderService w **połączeń** okienka.  
  
3. OrderService kliknij prawym przyciskiem myszy i wybierz **Zarządzanie WCF i usługami WF**, **Konfigurowanie...** . **Konfigurowanie usług WCF i WF aplikacji** zostanie wyświetlone okno dialogowe.  
  
4. Wybierz **ogólne** kartę, aby wyświetlić ogólne informacje o aplikacji, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Karta Ogólne, okno dialogowe Konfiguracja sieci szkieletowej aplikacji](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-general.gif "AppFabricConfiguration — ogólne")  
  
5. Wybierz **monitorowanie** kartę. Zawiera różne ustawienia monitorowania, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Aplikacja monitorowanie konfiguracji sieci szkieletowej kartę](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration monitorowanie")  
  
     Aby uzyskać więcej informacji o konfigurowaniu usługi przepływu pracy monitorowania w sieci szkieletowej aplikacji zobacz [konfigurowania monitorowania przy użyciu rozwiązania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193153).  
  
6. Wybierz **trwałość przepływu pracy** kartę. Dzięki temu można skonfigurować aplikację do używania App Fabric domyślne trwałość dostawcy jak pokazano na poniższym zrzucie ekranu.  
  
     ![Konfiguracja aplikacji w sieci szkieletowej &#45; trwałości](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-persistence.gif "AppFabricConfiguration trwałości")  
  
     Aby uzyskać więcej informacji o konfigurowaniu trwałości przepływu pracy w AppFabric w systemie Windows Server, zobacz [Konfigurowanie trwałość przepływu pracy w sieci szkieletowej aplikacji](https://go.microsoft.com/fwlink/?LinkId=193148).  
  
7. Wybierz **przepływu pracy zarządzania hostem** kartę. Dzięki temu można określić, kiedy wystąpień usługi przepływu pracy bezczynności powinien być zwolnione i utrwalane, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Programu AppFabric w konfiguracji przepływu pracy zarządzania hostem](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-management.gif "AppFabricConfiguration zarządzania")  
  
     Aby uzyskać więcej informacji na temat konfiguracji zarządzania hosta przepływu pracy zobacz [konfigurowania zarządzania hostem przepływu pracy w sieci szkieletowej aplikacji](https://go.microsoft.com/fwlink/?LinkId=193151).  
  
8. Wybierz **Auto-Start** kartę. Dzięki temu można określić ustawienia automatycznego uruchamiania usługi przepływu pracy w aplikacji, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Zrzut ekranu pokazujący aplikacji Service Fabric automatycznie&#45;narzędzia konfiguracji.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-auto-start-configuration.gif)  
  
     Aby uzyskać więcej informacji o konfigurowaniu Auto-Start zobacz [Konfigurowanie automatycznego uruchamiania przy użyciu rozwiązania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193150).  
  
9. Wybierz **ograniczania** kartę. Dzięki temu można skonfigurować ustawienia ograniczania przepustowości usługi przepływu pracy, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Zrzut ekranu pokazujący App Fabric Konfiguracja ograniczania.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-throttling-configuration.gif)  
  
     Aby uzyskać więcej informacji na temat konfigurowania ograniczania zobacz [konfigurowania ograniczania przy użyciu rozwiązania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193149).  
  
10. Wybierz **zabezpieczeń** kartę. Dzięki temu można skonfigurować ustawienia zabezpieczeń dla aplikacji, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Konfiguracja zabezpieczeń aplikacji w sieci szkieletowej](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-security.gif "AppFabricConfiguration zabezpieczeń")  
  
     Aby uzyskać więcej informacji na temat konfigurowania zabezpieczeń przy użyciu rozwiązania Windows Server AppFabric zobacz [konfigurowania zabezpieczeń przy użyciu rozwiązania AppFabric](https://go.microsoft.com/fwlink/?LinkId=193152).  
  
### <a name="using-windows-server-app-fabric"></a>Przy użyciu systemu Windows Server AppFabric  
  
1. Kompiluj rozwiązanie, skopiuj niezbędne pliki do katalogu wirtualnego.  
  
2. Kliknij prawym przyciskiem myszy projekt OrderClient, a następnie wybierz pozycję **debugowania**, **Uruchom nowe wystąpienie** można uruchomić aplikacji klienckiej.  
  
3. Klient zostanie wykonane, a program Visual Studio wyświetli **ostrzeżenie o zabezpieczeniach dołączania** okno dialogowe, kliknij przycisk **nie dołączaj** przycisku. Oznacza to, Visual Studio, aby nie dołączać do procesu usługi IIS do debugowania.  
  
4. Aplikacja kliencka będzie powodują natychmiastowe wywołanie metody usługi przepływu pracy, a następnie poczekaj. Usługa przepływu pracy zostanie umieszczona w stanie bezczynności i utrwalone. Można to sprawdzić, uruchamianie programu Internet Information Services (inetmgr.exe), przechodząc do OrderService w okienku połączenia i wybierając ją. Następnie kliknij ikonę Pulpit nawigacyjny aplikacji Service Fabric, w okienku po prawej stronie. W ramach wystąpienia WF utrwalone zobaczysz, że istnieje jeden utrwalonego wystąpienia przepływu pracy usługi jak pokazano na poniższym zrzucie ekranu.  
  
     ![Zrzut ekranu przedstawiający pulpit nawigacyjny aplikacji Service Fabric.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-dashboard.gif)  
  
     **Historii wystąpienia WF** Wyświetla informacje na temat usługi przepływu pracy, takich jak liczbę aktywacji usługi przepływu pracy, liczba ukończenia wystąpienia usługi przepływu pracy i liczbę wystąpień przepływu pracy z błędami. W obszarze aktywności lub bezczynności wystąpienia, zostaną wyświetlone łącze kliknięcie łącza spowoduje wyświetlenie więcej informacji na temat wystąpienia bezczynności przepływu pracy, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Zrzut ekranu pokazujący utrwalone Szczegóły wystąpienia przepływu pracy.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/persisted-workflow-instance-detail.gif)  
  
     Aby uzyskać więcej informacji na temat systemu Windows Server AppFabric funkcji i jak ich używać, zobacz [hostingu funkcje systemu Windows Server App Service Fabric](https://go.microsoft.com/fwlink/?LinkID=193143&clcid=0x409)  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie długo działającej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=193143)
- [Instalowanie systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=193136)
- [Dokumentacja programu systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=193037&clcid=0x409)
