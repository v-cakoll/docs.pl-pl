---
title: 'Instrukcje: Hostowanie usługi WCF w usłudze zarządzanej systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: 698a5134683341fedf2a37f7d6383770e14c232c
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964801"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a>Instrukcje: Hostowanie usługi WCF w usłudze zarządzanej systemu Windows

W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia usługi Windows Communication Foundation (WCF) hostowanej przez usługę systemu Windows. Ten scenariusz jest włączany przez opcję hostingu zarządzanej usługi systemu Windows, która jest długotrwałą usługą WCF hostowaną poza Internet Information Services (IIS) w bezpiecznym środowisku, które nie jest uaktywniane przez komunikat. Okres istnienia usługi jest kontrolowany przez system operacyjny. Ta opcja hostingu jest dostępna we wszystkich wersjach systemu Windows.

Usługami systemu Windows można zarządzać za pomocą przystawki Microsoft. ManagementConsole. SnapIn w programie Microsoft Management Console (MMC) i można ją skonfigurować do automatycznego uruchamiania podczas uruchamiania systemu. Ta opcja hostingu polega na zarejestrowaniu domeny aplikacji (AppDomain), która hostuje usługę WCF jako usługę zarządzaną systemu Windows, dzięki czemu okres istnienia usługi jest kontrolowany przez menedżera kontroli usług (SCM) dla usług systemu Windows.

Kod usługi zawiera implementację usługi kontraktu usługi, klasy usługi systemu Windows i klasy Instalatora. Klasa implementacji usługi, `CalculatorService`, jest usługą WCF. `CalculatorWindowsService` to usługa systemu Windows. Aby można było zakwalifikować jako usługę systemu Windows, Klasa dziedziczy po `ServiceBase` i implementuje metody `OnStart` i `OnStop`. W `OnStart`jest tworzony <xref:System.ServiceModel.ServiceHost> dla typu `CalculatorService` i otwarty. W `OnStop`usługa zostanie zatrzymana i usunięta. Host jest również odpowiedzialny za podanie adresu podstawowego dla hosta usługi, który został skonfigurowany w ustawieniach aplikacji. Klasa Instalatora, która dziedziczy po <xref:System.Configuration.Install.Installer>, umożliwia zainstalowanie programu jako usługi systemu Windows za pomocą narzędzia Installutil. exe.

## <a name="construct-the-service-and-provide-the-hosting-code"></a>Konstruowanie usługi i dostarczanie kodu hostingu

1. Utwórz nowy projekt **aplikacji konsoli** programu Visual Studio o nazwie **Usługa**.

2. Zmień nazwę Program.cs na Service.cs.

3. Zmień przestrzeń nazw na `Microsoft.ServiceModel.Samples`.

4. Dodaj odwołania do następujących zestawów:

    - System.ServiceModel.dll

    - System.ServiceProcess.dll

    - System.Configuration.Install.dll

5. Dodaj następujące instrukcje using do Service.cs.

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. Zdefiniuj kontrakt usługi `ICalculator`, jak pokazano w poniższym kodzie.

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. Zaimplementuj kontrakt usługi w klasie o nazwie `CalculatorService`, jak pokazano w poniższym kodzie.

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. Utwórz nową klasę o nazwie `CalculatorWindowsService` która dziedziczy z klasy <xref:System.ServiceProcess.ServiceBase>. Dodaj zmienną lokalną o nazwie `serviceHost`, aby odwołać się do wystąpienia <xref:System.ServiceModel.ServiceHost>. Zdefiniuj metodę `Main`, która wywołuje `ServiceBase.Run(new CalculatorWindowsService)`

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. Zastąp metodę <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, tworząc i otwierając nowe wystąpienie <xref:System.ServiceModel.ServiceHost>, jak pokazano w poniższym kodzie.

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. Zastąp <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metodę zamykającą <xref:System.ServiceModel.ServiceHost>, jak pokazano w poniższym kodzie.

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. Utwórz nową klasę o nazwie `ProjectInstaller`, która dziedziczy po <xref:System.Configuration.Install.Installer> i która jest oznaczona za pomocą <xref:System.ComponentModel.RunInstallerAttribute> ustawionej na `true`. Dzięki temu można zainstalować usługę systemu Windows za pomocą narzędzia Installutil. exe.

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. Usuń klasę `Service`, która została wygenerowana podczas tworzenia projektu.

13. Dodaj plik konfiguracji aplikacji do projektu. Zastąp zawartość pliku następującym kodem XML konfiguracji.

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

     Kliknij prawym przyciskiem myszy plik App. config w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. W obszarze **Kopiuj do katalogu wyjściowego** wybierz opcję **Kopiuj, jeśli nowszy**.

     Ten przykład jawnie określa punkty końcowe w pliku konfiguracji. Jeśli nie dodasz żadnych punktów końcowych do usługi, środowisko uruchomieniowe doda domyślne punkty końcowe. W tym przykładzie, ponieważ usługa ma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ustawioną na `true`, usługa ma także włączone metadane publikowania. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

## <a name="install-and-run-the-service"></a>Instalowanie i uruchamianie usługi

1. Skompiluj rozwiązanie, aby utworzyć `Service.exe` plik wykonywalny.

2. Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio i przejdź do katalogu projektu. Wpisz `installutil bin\service.exe` w wierszu polecenia, aby zainstalować usługę systemu Windows.

     Wpisz `services.msc` w wierszu polecenia, aby uzyskać dostęp do Menedżera sterowania usługami (SCM). Usługa systemu Windows powinna być wyświetlana w usługach jako "WCFWindowsServiceSample". Usługa WCF może odpowiedzieć tylko na klientów, jeśli usługa systemu Windows jest uruchomiona. Aby uruchomić usługę, kliknij ją prawym przyciskiem myszy w SCM i wybierz polecenie "Start" lub wpisz **net start WCFWindowsServiceSample** w wierszu polecenia.

3. Jeśli wprowadzisz zmiany w usłudze, musisz je najpierw zatrzymać i odinstalować. Aby zatrzymać usługę, kliknij prawym przyciskiem myszy usługę w SCM i wybierz pozycję "Zatrzymaj" lub **wpisz net stop WCFWindowsServiceSample** w wierszu polecenia. Należy pamiętać, że w przypadku zatrzymania usługi systemu Windows, a następnie uruchomienia klienta <xref:System.ServiceModel.EndpointNotFoundException> wyjątek występuje, gdy klient próbuje uzyskać dostęp do usługi. Aby odinstalować typ usługi systemu Windows **Installutil/u bin\service.exe** w wierszu polecenia.

## <a name="example"></a>Przykład

Poniżej znajduje się kompletna lista kodu używanego w tym temacie:

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

Podobnie jak w przypadku opcji "samohosting" środowisko hostingu usług systemu Windows wymaga, aby część kodu hostingu była zapisywana jako część aplikacji. Usługa jest zaimplementowana jako Aplikacja konsolowa i zawiera swój własny kod hostingu. W innych środowiskach hostingu, takich jak usługa aktywacji procesów systemu Windows (WAS) w programie Internet Information Services (IIS), deweloperzy nie muszą pisać kodu hostingu.

## <a name="see-also"></a>Zobacz także

- [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)
- [Hosting w aplikacji zarządzanej](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)
- [Usługi hostingowe](../../../../docs/framework/wcf/hosting-services.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
