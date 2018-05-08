---
title: 'Porady: Konfigurowanie ustawień usług COM +'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: 43964331f6728db0f094eaceb63e2c306d2dd3ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-com-service-settings"></a>Porady: Konfigurowanie ustawień usług COM +
Interfejs aplikacji jest dodania lub usunięcia za pomocą narzędzia konfiguracji usług COM +, konfiguracji usługi sieci Web jest aktualizowana w pliku konfiguracji aplikacji. W trybie COM + hostowanej pliku Application.config znajduje się w katalogu głównym aplikacji (aplikacje %PROGRAMFILES%\ComPlus\\{appid} jest ustawieniem domyślnym). W obu trybach hostowanych w sieci Web w katalogu określonego vroot znajduje się plik Web.config.  
  
> [!NOTE]
>  Podpisywanie komunikatów należy chronić je przed naruszeniem wiadomości między klientem a serwerem. Można również używać szyfrowania warstwy transportu lub wiadomości do ochrony przed ujawnieniem informacji z wiadomości między klientem serwerem. Podobnie jak w przypadku usług Windows Communication Foundation (WCF), należy używać ograniczania ograniczyć liczbę współbieżnych wywołań, połączeń, wystąpienia i oczekujących operacji. Pomaga to zapobiec nadmierne zużycie zasobów. Ograniczanie zachowanie jest określany za pośrednictwem ustawień pliku konfiguracji usługi.  
  
## <a name="example"></a>Przykład  
 Należy wziąć pod uwagę składnika, który implementuje interfejs następujące:  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 Jeśli składnik jest udostępniany jako usługa sieci Web, odpowiednich kontraktu usługi, które będzie widoczne, a klienci musi być zgodne, jest następujący:  
  
```  
[ServiceContract(Session = true,  
Namespace = "http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7",  
Name = "IFinances")]  
public interface IFinancesContract : IDisposable  
{  
    [OperationContract]  
    string Debit(string accountNo, double amount);  
    [OperationContract]  
    string Credit(string accountNo, double amount);  
}  
```  
  
> [!NOTE]
>  Identyfikator IID stanowi część początkowej przestrzeń nazw kontraktu.  
  
 Aplikacje klienckie, które używają tej usługi musi być zgodna z tym kontraktem, oraz za pomocą powiązania, który jest zgodny z określoną w konfiguracji aplikacji.  
  
 Poniższy przykład kodu pokazuje domyślny plik konfiguracji. Usługi sieci Web Windows Communication Foundation (WCF), to odpowiada schemat konfiguracji modelu usług standardowa i można je edytować w taki sam sposób jak inne pliki konfiguracji usługi WCF.  
  
 Typowy modyfikacje obejmują:  
  
-   Zmiana adresu punktu końcowego z domyślnego formularza ApplicationName/NazwaSkładnika/InterfaceName na bardziej użytecznej postaci.  
  
-   Modyfikowanie przestrzeni nazw usługi z domyślnego "http://tempuri.org/InterfaceID" formularza, aby lepiej dopasowane formularza.  
  
-   Zmiana punktu końcowego do użycia powiązania innego transportu.  
  
     W modelu COM +-hostowanej przypadku transportu nazwanych potoków jest używany domyślnie, ale można zamiast tego użyć transportu poza maszyny, podobnie jak protokół TCP.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="comNonTransactionalBinding" />  
                <binding name="comTransactionalBinding" transactionFlow="true" />  
            </netNamedPipeBinding>  
        </bindings>  
        <comContracts>  
            <comContract contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"  
                name="IFinances" namespace="http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7"  
                requiresSession="true">  
                <exposedMethods>  
                    <add exposedMethod="Debit" />  
                    <add exposedMethod="Credit" />  
                </exposedMethods>  
            </comContract>  
        </comContracts>  
        <services>  
            <service name="{DCDB24CC-0B19-4534-95CD-FBBFF4D67DD9},{C942B840-AD54-4A44-B5F7-928130980AB9}">  
                <endpoint address="IFinances" binding="netNamedPipeBinding" bindingConfiguration="comNonTransactionalBinding"  
                    contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" />  
                <host>  
                    <baseAddresses>  
                        <add baseAddress="net.pipe://localhost/ServiceModelDocSampleApp/ServiceModelDocSample.esFinance" />  
                    </baseAddresses>  
                </host>  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z aplikacjami COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
