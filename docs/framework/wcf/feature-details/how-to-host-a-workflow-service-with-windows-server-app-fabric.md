---
title: 'Instrukcje: Hostowanie usługi przepływu pracy przy użyciu rozwiązania AppFabric w systemie Windows Server'
ms.date: 03/30/2017
ms.assetid: 83b62cce-5fc2-4c6d-b27c-5742ba3bac73
ms.openlocfilehash: ecc7a954b2d88cdbcf934cc836e9ad6e3ef7ed52
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964762"
---
# <a name="how-to-host-a-workflow-service-with-windows-server-app-fabric"></a>Instrukcje: Hostowanie usługi przepływu pracy przy użyciu rozwiązania AppFabric w systemie Windows Server

Hostowanie usług przepływu pracy w usłudze App Fabric jest podobne do hostingu w ramach usług IIS/WAS. Jedyną różnicą jest to, że narzędzia sieci szkieletowej aplikacji umożliwiają wdrażanie i monitorowanie usług przepływu pracy oraz zarządzanie nimi. W tym temacie jest używana usługa przepływu pracy utworzona w trakcie [tworzenia długotrwałej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md). Ten temat przeprowadzi Cię przez proces tworzenia usługi przepływu pracy. W tym temacie opisano sposób hostowania usługi przepływu pracy przy użyciu sieci szkieletowej aplikacji. Aby uzyskać więcej informacji na temat sieci szkieletowej aplikacji systemu Windows Server, zobacz [dokumentację sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)). Przed wykonaniem poniższych kroków upewnij się, że masz zainstalowaną sieć szkieletową aplikacji systemu Windows Server.  Aby to zrobić, otwórz Internet Information Services (inetmgr. exe), kliknij nazwę serwera w widoku **połączenia** , kliknij przycisk lokacje, a następnie kliknij pozycję **Domyślna witryna sieci Web**. Po prawej stronie ekranu powinna zostać wyświetlona sekcja o nazwie **App Fabric**. Jeśli nie widzisz tej sekcji (zostanie ona w górnej części okienka po prawej stronie), nie masz zainstalowanej sieci szkieletowej aplikacji. Aby uzyskać więcej informacji na temat instalowania sieci szkieletowej aplikacji systemu Windows Server, zobacz [Instalowanie sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee790960(v=azure.10)).  
  
### <a name="creating-a-simple-workflow-service"></a>Tworzenie prostej usługi przepływu pracy  
  
1. Otwórz program Visual Studio 2012 i Załaduj rozwiązanie OrderProcessing utworzone w temacie [Tworzenie długotrwałej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md) .  
  
2. Kliknij prawym przyciskiem myszy projekt **OrderService** i wybierz pozycję **Właściwości** , a następnie wybierz kartę **Sieć Web** .  
  
3. W sekcji **Akcja początkowa** na stronie właściwości wybierz **określoną stronę** i wpisz Service1. xamlx w polu edycji.  
  
4. W sekcji **serwery** na stronie właściwości wybierz opcję **Użyj lokalnego serwera sieci Web IIS** i wpisz następujący adres URL: `http://localhost/OrderService`.  
  
5. Kliknij przycisk **Utwórz katalog wirtualny** . Spowoduje to utworzenie nowego katalogu wirtualnego i skonfigurowanie projektu w celu skopiowania plików wymaganych do katalogu wirtualnego po skompilowaniu projektu.  Alternatywnie można ręcznie skopiować plik. xamlx, Web. config i wszystkie potrzebne biblioteki DLL do katalogu wirtualnego.  
  
### <a name="configuring-a-workflow-service-hosted-in-windows-server-app-fabric"></a>Konfigurowanie usługi przepływu pracy hostowanej w sieci szkieletowej aplikacji systemu Windows Server  
  
1. Otwórz Menedżera Internet Information Services (inetmgr. exe).  
  
2. Przejdź do katalogu wirtualnego OrderService w okienku **połączenia** .  
  
3. Kliknij prawym przyciskiem myszy pozycję OrderService i wybierz pozycję **Zarządzaj usługami WCF i WF**, **Skonfiguruj...** . Zostanie wyświetlone okno dialogowe **Konfigurowanie WCF i WF dla aplikacji** .  
  
4. Wybierz kartę **Ogólne** , aby wyświetlić ogólne informacje o aplikacji, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Karta Ogólne w oknie dialogowym konfiguracji sieci szkieletowej aplikacji](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-general.gif "AppFabricConfiguration — ogólne")  
  
5. Wybierz kartę **monitorowanie** . Przedstawiono w nim różne ustawienia monitorowania, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Karta monitorowanie konfiguracji sieci szkieletowej aplikacji](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-monitoring.gif "AppFabricConfiguration — monitorowanie")  
  
     Aby uzyskać więcej informacji na temat konfigurowania monitorowania usługi przepływu pracy w usłudze App Fabric, zobacz [konfigurowanie monitorowania przy użyciu sieci szkieletowej aplikacji](https://docs.microsoft.com/previous-versions/appfabric/ee677384(v=azure.10)).  
  
6. Wybierz kartę **trwałość przepływu pracy** . Dzięki temu można skonfigurować aplikację do korzystania z domyślnego dostawcy trwałości sieci szkieletowej aplikacji, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Trwałość konfiguracji &#45; sieci szkieletowej aplikacji](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-persistence.gif "AppFabricConfiguration — trwałość")  
  
     Aby uzyskać więcej informacji o konfigurowaniu trwałości przepływu pracy w sieci szkieletowej systemu Windows Server, zobacz [Konfigurowanie trwałości przepływu pracy w sieci szkieletowej aplikacji](https://docs.microsoft.com/previous-versions/appfabric/ee677353(v=azure.10)).  
  
7. Wybierz kartę **Zarządzanie hostem przepływu pracy** . Pozwala to określić, kiedy bezczynne wystąpienia usługi przepływu pracy powinny być zwolnione i utrwalane, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Zarządzanie hostem przepływu pracy konfiguracji sieci szkieletowej aplikacji](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-management.gif "AppFabricConfiguration — zarządzanie")  
  
     Aby uzyskać więcej informacji na temat konfiguracji zarządzania hostem przepływu pracy, zobacz [Konfigurowanie zarządzania hostem przepływu pracy w usłudze App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ff383424(v=azure.10)).  
  
8. Wybierz kartę **Autostart** . Pozwala to określić ustawienia Autostart dla usług przepływu pracy w aplikacji, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Zrzut ekranu pokazujący konfigurację automatycznej&#45;konfiguracji sieci szkieletowej aplikacji.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-auto-start-configuration.gif)  
  
     Więcej informacji o konfigurowaniu autostartu można znaleźć w temacie [Configuring Autostart with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677261(v=azure.10)).  
  
9. Wybierz kartę **ograniczanie przepustowości** . Dzięki temu można skonfigurować ustawienia ograniczania dla usługi przepływu pracy, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Zrzut ekranu przedstawiający konfigurację ograniczania przepustowości sieci szkieletowej aplikacji.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-throttling-configuration.gif)  
  
     Aby uzyskać więcej informacji o konfigurowaniu ograniczania przepustowości, zobacz [konfigurowanie ograniczania przy użyciu sieci szkieletowej aplikacji](https://docs.microsoft.com/previous-versions/appfabric/ee677261(v=azure.10)).  
  
10. Wybierz kartę **zabezpieczenia** . Dzięki temu można skonfigurować ustawienia zabezpieczeń dla aplikacji, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Konfiguracja zabezpieczeń sieci szkieletowej aplikacji](../../../../docs/framework/wcf/feature-details/media/appfabricconfiguration-security.gif "AppFabricConfiguration — zabezpieczenia")  
  
     Więcej informacji o konfigurowaniu zabezpieczeń przy użyciu sieci szkieletowej aplikacji systemu Windows Server można znaleźć w temacie [Configuring Security with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677278(v=azure.10)).  
  
### <a name="using-windows-server-app-fabric"></a>Korzystanie z sieci szkieletowej aplikacji systemu Windows Server  
  
1. Skompiluj rozwiązanie, aby skopiować niezbędne pliki do katalogu wirtualnego.  
  
2. Kliknij prawym przyciskiem myszy projekt OrderClient i wybierz polecenie **Debuguj**, **Uruchom nowe wystąpienie** , aby uruchomić aplikację kliencką.  
  
3. Zostanie uruchomiony klient programu, a program Visual Studio wyświetli okno dialogowe **dołączanie ostrzeżenia zabezpieczeń** , a następnie kliknij przycisk **nie dołączania** . Oznacza to, że program Visual Studio nie zostanie dołączony do procesu usług IIS w celu debugowania.  
  
4. Aplikacja kliencka natychmiast wywoła usługę przepływu pracy, a następnie zaczeka. Usługa przepływu pracy przejdzie w stan bezczynności i zostanie utrwalona. Można to sprawdzić, uruchamiając Internet Information Services (inetmgr. exe), przechodząc do OrderService w okienku połączenia i wybierając je. Następnie kliknij ikonę pulpitu nawigacyjnego aplikacji sieci szkieletowej w okienku po prawej stronie. W obszarze utrwalone wystąpienia WF zobaczysz jedno trwałe wystąpienie usługi przepływu pracy, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Zrzut ekranu przedstawiający pulpit nawigacyjny aplikacji sieci szkieletowej.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/app-fabric-dashboard.gif)  
  
     **Historia wystąpienia WF** zawiera listę informacji o usłudze przepływu pracy, takich jak liczba aktywacji usługi przepływu pracy, liczba ukończonych wystąpień usługi przepływu pracy oraz liczba wystąpień przepływów pracy z błędami. W obszarze aktywne lub bezczynne wystąpienia zostanie wyświetlone łącze. kliknięcie linku spowoduje wyświetlenie więcej informacji o wystąpieniach bezczynności przepływu pracy, jak pokazano na poniższym zrzucie ekranu.  
  
     ![Zrzut ekranu przedstawiający utrwalone szczegóły wystąpienia przepływu pracy.](./media/how-to-host-a-workflow-service-with-windows-server-app-fabric/persisted-workflow-instance-detail.gif)  
  
     Aby uzyskać więcej informacji o funkcjach sieci szkieletowej systemu Windows Server i sposobach ich użycia, zobacz [funkcje hostingu usługi Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie długo działającej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
- [Instalowanie sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee790960(v=azure.10))
- [Dokumentacja sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10))
