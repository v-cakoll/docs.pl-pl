---
title: 'Instrukcje: Hostowanie usługi WCF w usłudze zarządzanej systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: c6c3e057fd07569d462f1bf25d1c283e42024a8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a>Instrukcje: Hostowanie usługi WCF w usłudze zarządzanej systemu Windows
W tym temacie przedstawiono podstawowe czynności wymagane do tworzenia usług Windows Communication Foundation (WCF), obsługiwanej przez usługę systemu Windows. Scenariusz jest włączone przez usługę systemu Windows zarządzany hosting opcję długotrwałe usługi WCF hostowanej poza Internet Information Services (IIS) w bezpiecznym środowisku, który nie jest aktywowany wiadomości. Okres istnienia usługi steruje zamiast tego systemu operacyjnego. Ta opcja obsługi jest dostępna we wszystkich wersjach systemu Windows.  
  
 Usługi systemu Windows można zarządzać za pomocą Microsoft.ManagementConsole.SnapIn w konsoli Microsoft Management Console (MMC) i można skonfigurować tak, aby uruchamiała się automatycznie, gdy system jest uruchamiany. Ta opcja hostingu składa się z rejestrowania domeny aplikacji (AppDomain), który jest hostem usługi WCF jako zarządzanych usług systemu Windows tak, aby okres istnienia procesu usługi jest kontrolowany przez Menedżera sterowania usługami (SCM) dla usług systemu Windows.  
  
 Kod usługi zawiera implementacji usługi, kontrakt usługi, klasa usługi systemu Windows i klasę Instalatora. Klasa implementacji usługi, `CalculatorService`, to usługa WCF. `CalculatorWindowsService` To usługa systemu Windows. Aby zakwalifikować się jako usługa systemu Windows, dziedziczy po klasie `ServiceBase` i implementuje `OnStart` i `OnStop` metody. W `OnStart`, <xref:System.ServiceModel.ServiceHost> jest tworzona dla `CalculatorService` wpisz i otworzyć. W `OnStop`, że usługa jest zatrzymana i usunięty. Host jest również odpowiedzialność za zapewnienie adres podstawowy hosta usługi, który został skonfigurowany w ustawieniach aplikacji. Instalator klasy, która dziedziczy <xref:System.Configuration.Install.Installer>, pozwala programowi zainstalowania przez narzędzie Installutil.exe jako usługa systemu Windows.  
  
### <a name="construct-the-service-and-provide-the-hosting-code"></a>Konstruowania usługi i podaj kod hostingu  
  
1.  Utwórz nowy projekt aplikacji konsoli w usłudze Visual Studio o nazwie "Usługa".  
  
2.  Zmień nazwę pliku Program.cs Service.cs.  
  
3.  Zmienić przestrzeni nazw do Microsoft.ServiceModel.Samples.  
  
4.  Dodaj odwołania do następujących zestawów.  
  
    -   System.ServiceModel.dll  
  
    -   System.ServiceProcess.dll  
  
    -   System.Configuration.Install.dll  
  
5.  Dodaj następujące instrukcje using do Service.cs.  
  
     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]  
  
6.  Zdefiniuj `ICalculator` kontraktu usługi, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]  
  
7.  Implementowanie kontraktu usługi w klasie o nazwie `CalculatorService` jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]  
  
8.  Utwórz nową klasę o nazwie `CalculatorWindowsService` dziedziczący po <xref:System.ServiceProcess.ServiceBase> klasy. Dodawanie zmiennej lokalnej o nazwie `serviceHost` do odwołania <xref:System.ServiceModel.ServiceHost> wystąpienia. Zdefiniuj `Main` metodę, która wywołuje `ServiceBase.Run(new CalculatorWindowsService)`  
  
     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]  
  
9. Zastąpienie <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metody tworzenia i otwierania nowych <xref:System.ServiceModel.ServiceHost> wystąpienie, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]  
  
10. Zastąpienie <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metoda zamknięcia <xref:System.ServiceModel.ServiceHost> jak pokazano w poniższym kodzie.  
  
     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]  
  
11. Utwórz nową klasę o nazwie `ProjectInstaller` dziedziczący po <xref:System.Configuration.Install.Installer> i który jest oznaczony atrybutem <xref:System.ComponentModel.RunInstallerAttribute> ustawioną `true`. Dzięki temu można zainstalować przez narzędzie Installutil.exe usługi systemu Windows.  
  
     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]  
  
12. Usuń `Service` klasy, który został wygenerowany podczas tworzenia projektu.  
  
13. Dodaj plik konfiguracji aplikacji do projektu. Zastąp zawartość pliku o następującej konfiguracji XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>    <services>  
          <!-- This section is optional with the new configuration model  
               introduced in .NET Framework 4. -->  
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                   behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
            <endpoint address=""  
                      binding="wsHttpBinding"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
          </service>  
        </services>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceMetadata httpGetEnabled="true"/>  
              <serviceDebug includeExceptionDetailInFaults="False"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Kliknij prawym przyciskiem myszy w pliku App.config **Eksploratora rozwiązań** i wybierz **właściwości**. W obszarze **Kopiuj do katalogu wyjściowego** wybierz **Kopiuj, jeśli nowszy**.  
  
     W tym przykładzie jawnie określa punkty końcowe w pliku konfiguracji. Jeśli nie dodawaj żadnych punktów końcowych do usługi, środowisko uruchomieniowe dodaje domyślne punkty końcowe. W tym przykładzie ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ustawioną `true`, usługa ma również publikowanie metadanych włączone. Aby uzyskać więcej informacji na temat domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
### <a name="install-and-run-the-service"></a>Zainstaluj i uruchom usługę  
  
1.  Utworzenie rozwiązania do tworzenia `Service.exe` pliku wykonywalnego.  
  
2.  Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersz polecenia i przejdź do katalogu projektu. Typ `installutil bin\service.exe` w wierszu polecenia, aby zainstalować usługę systemu Windows.  
  
    > [!NOTE]
    >  Jeśli nie używasz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersz polecenia, upewnij się, że `%WinDir%\Microsoft.NET\Framework\v4.0.<current version>` katalog znajduje się w ścieżce systemowej.  
  
     Typ `services.msc` w wierszu polecenia można uzyskać dostępu do Menedżera sterowania usługami (SCM). Usługa systemu Windows powinna pojawić się w usługach jako "WCFWindowsServiceSample". Usługi WCF może odpowiadać tylko na klientach, jeśli usługa systemu Windows jest uruchomiona. Aby uruchomić usługę, kliknij prawym przyciskiem myszy go w SCM i wybierz polecenie "Start" lub typu **net start WCFWindowsServiceSample** w wierszu polecenia.  
  
3.  Jeśli wprowadzisz zmiany do usługi należy najpierw zatrzymaj ją i go odinstalować. Aby zatrzymać usługę, kliknij prawym przyciskiem myszy usługi w SCM i wybierz pozycję stop (Zatrzymaj)", lub **typu net stop WCFWindowsServiceSample** w wierszu polecenia. Należy pamiętać, że jeśli zatrzymać usługi systemu Windows, a następnie uruchom klienta, <xref:System.ServiceModel.EndpointNotFoundException> wyjątek występuje, gdy klient próbuje uzyskać dostęp do usługi. Aby odinstalować typu usługi systemu Windows **installutil /u bin\service.exe** w wierszu polecenia.  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełna lista kod używany w tym temacie.  
  
 [!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
 [!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]  
  
 Podobnie jak opcji "Własnym hostingu" Usługa systemu Windows obsługującego środowisko wymaga, że niektóre hostingu kodu można zapisywać w ramach aplikacji. Usługa jest zaimplementowany jako aplikacji konsoli i zawiera własną hostingu kod. W innych środowiskach hostingu, na przykład w Internet informacji Services (IIS), obsługa usługi aktywacji procesów systemu Windows (WAS) nie jest konieczne deweloperom pisanie hosting kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)  
 [Hosting w aplikacji zarządzanej](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)  
 [Usługi hostingowe](../../../../docs/framework/wcf/hosting-services.md)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
