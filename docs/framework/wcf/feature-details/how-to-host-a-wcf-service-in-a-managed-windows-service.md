---
title: 'Instrukcje: Hostowanie usługi WCF w usłudze zarządzanej systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: b4cb2ae3b2db8cdfab962c61ead387baf1bb7158
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613831"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a>Instrukcje: Hostowanie usługi WCF w usłudze zarządzanej systemu Windows

W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia usługi Windows Communication Foundation (WCF), która jest hostowana przez usługę Windows. Scenariusz jest włączone przez usługę Windows zarządzanego hostingu opcję długotrwałych usługi WCF hostowane poza Internet Information Services (IIS) w bezpiecznym środowisku, który nie jest aktywowany komunikat o. Okres istnienia usługi steruje zamiast tego systemu operacyjnego. Ta opcja hostingu jest dostępny we wszystkich wersjach systemu Windows.

Usługi Windows można zarządzać za pomocą Microsoft.ManagementConsole.SnapIn w konsoli Microsoft Management Console (MMC) i można skonfigurować, aby uruchamiała się automatycznie, gdy system jest uruchamiany. Ta opcja hostingu składa się z rejestracji domeny aplikacji (AppDomain), który jest hostem usługi WCF jako usługa zarządzana Windows tak, że okres istnienia procesu usługi jest kontrolowany przez Menedżera sterowania usługami (SCM) dla usług Windows.

Kod usługi obejmuje z implementacją kontraktu usługi, usługa Windows klasy, a Instalator usługi. Klasa implementacji usługi, `CalculatorService`, to usługa WCF. `CalculatorWindowsService` Usługa Windows. Aby zakwalifikować się jako usługa Windows, klasa dziedziczy `ServiceBase` i implementuje `OnStart` i `OnStop` metody. W `OnStart`, <xref:System.ServiceModel.ServiceHost> jest tworzona dla `CalculatorService` wpisz i otwarty. W `OnStop`, usługa jest zatrzymany i usunięty. Host jest również odpowiedzialny za zapewnienie adres podstawowy host usługi, który został skonfigurowany w ustawieniach aplikacji. Klasa Instalatora, która dziedziczy z <xref:System.Configuration.Install.Installer>, pozwala programowi na narzędzie Installutil.exe instaluje jako usługę Windows.

## <a name="construct-the-service-and-provide-the-hosting-code"></a>Utworzyć usługę i podaj kod hostingu

1.  Tworzenie nowego programu Visual Studio **aplikacja Konsolowa** projekt o nazwie **usługi**.

2.  Zmień nazwę pliku Program.cs Service.cs.

3.  Zmień przestrzeń nazw w celu `Microsoft.ServiceModel.Samples`.

4.  Dodaj odwołania do następujących zestawów:

    - System.ServiceModel.dll

    - System.ServiceProcess.dll

    - System.Configuration.Install.dll

5.  Dodaj następujące instrukcje using do Service.cs.

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6.  Zdefiniuj `ICalculator` kontraktu usługi, jak pokazano w poniższym kodzie.

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7.  Implementowanie kontraktu usługi w klasie o nazwie `CalculatorService` jak pokazano w poniższym kodzie.

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8.  Utwórz nową klasę o nazwie `CalculatorWindowsService` tej, która dziedziczy <xref:System.ServiceProcess.ServiceBase> klasy. Dodawanie zmiennej lokalnej o nazwie `serviceHost` do odwołania <xref:System.ServiceModel.ServiceHost> wystąpienia. Zdefiniuj `Main` metodę, która wywołuje `ServiceBase.Run(new CalculatorWindowsService)`

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. Zastąp <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> metody tworzenia i otwierania nowych <xref:System.ServiceModel.ServiceHost> wystąpienia tak jak pokazano w poniższym kodzie.

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. Zastąp <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metoda zamknięcia <xref:System.ServiceModel.ServiceHost> jak pokazano w poniższym kodzie.

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. Utwórz nową klasę o nazwie `ProjectInstaller` tej, która dziedziczy <xref:System.Configuration.Install.Installer> , oznaczony za pomocą <xref:System.ComponentModel.RunInstallerAttribute> równa `true`. Dzięki temu usługa Windows do zainstalowania przez narzędzie Installutil.exe.

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

     Kliknij prawym przyciskiem myszy pliku App.config w **Eksploratora rozwiązań** i wybierz **właściwości**. W obszarze **Kopiuj do katalogu wyjściowego** wybierz **Kopiuj Jeśli nowszy**.

     Ten przykład jawnie określa punkty końcowe w pliku konfiguracji. Jeśli nie dodasz żadnych punktów końcowych do usługi, środowiska uruchomieniowego dodaje domyślne punkty końcowe. W tym przykładzie ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> równa `true`, usługi ma także publikowanie metadanych włączone. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

## <a name="install-and-run-the-service"></a>Zainstaluj i uruchom usługę

1.  Kompiluj rozwiązanie, aby utworzyć `Service.exe` pliku wykonywalnego.

2.  Otwórz wiersz polecenia dla deweloperów programu Visual Studio i przejdź do katalogu projektu. Typ `installutil bin\service.exe` w wierszu polecenia, aby zainstalować usługę Windows.

     Typ `services.msc` na dostęp do Menedżera sterowania usługami (SCM), w wierszu polecenia. Usługa Windows widoczny na usługi jako "WCFWindowsServiceSample". Usługi WCF tylko może odpowiadać na klientach, jeśli usługa Windows jest uruchomiona. Aby uruchomić usługę, kliknij prawym przyciskiem myszy go w funkcji SCM i wybierz opcję "Start" lub typu **net start WCFWindowsServiceSample** w wierszu polecenia.

3.  Jeśli wprowadzisz zmiany w usłudze możesz zatrzymać go i jego odinstalowania. Aby zatrzymać usługę, kliknij prawym przyciskiem myszy usługę, w Menedżer sterowania usługami i wybierz opcję "Zatrzymaj" lub **typu net stop WCFWindowsServiceSample** w wierszu polecenia. Należy pamiętać, że jeśli Zatrzymaj usługę Windows, a następnie z klientem, <xref:System.ServiceModel.EndpointNotFoundException> wystąpi wyjątek, gdy klient próbuje uzyskać dostęp do usługi. Aby odinstalować typ usługi Windows **installutil /u bin\service.exe** w wierszu polecenia.

## <a name="example"></a>Przykład

Poniżej przedstawiono pełną listę kod używany w tym temacie:

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

Podobnie jak opcji "Własnym hostingu" usługi Windows Środowisko hostingu wymaga, że jakiś kod hostingu zapisywane jako część aplikacji. Ta usługa jest implementowany jako aplikację konsolową w języku i zawiera swój własny kod hostingu. W innych środowiskach hostingu, takich jak Windows Process Activation Service (WAS) hostingu w Internet Information Services (IIS), nie jest konieczne dla deweloperów napisać kod hostingu.

## <a name="see-also"></a>Zobacz także

- [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)
- [Hosting w aplikacji zarządzanej](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)
- [Usługi hostingowe](../../../../docs/framework/wcf/hosting-services.md)
- [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=201276)