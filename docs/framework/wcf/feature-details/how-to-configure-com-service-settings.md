---
title: 'Porady: Konfigurowanie ustawień usługi COM +'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: d14fd1434cb87dc62babeabb79cb780e568aacb7
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085875"
---
# <a name="how-to-configure-com-service-settings"></a>Porady: Konfigurowanie ustawień usługi COM +
Interfejs aplikacji są dodawane lub usuwane za pomocą narzędzia konfiguracji usług COM +, konfiguracji usługi sieci Web jest aktualizowana w pliku konfiguracji aplikacji. W trybie hostowanej modelu COM + plik Application.config jest umieszczany w katalogu głównym aplikacji (aplikacje %PROGRAMFILES%\ComPlus\\{appid} jest wartością domyślną). W obu trybach hostowanych w sieci Web w katalogu określonym vroot znajduje się plik Web.config.  
  
> [!NOTE]
>  Podpisywanie komunikatów należy chronić je przed naruszeniem wiadomości między klientem a serwerem. Wiadomości lub transportu szyfrowanie warstwy należy również chronić przed ujawnieniem informacji z komunikatów między klientem a serwerem. Podobnie jak w przypadku usług Windows Communication Foundation (WCF), należy używać ograniczania można ograniczyć liczbę współbieżnych wywołań, połączeń, wystąpienia i oczekujących operacji. Pozwala to zapobiec nadmiernego zużycia zasobów. Zachowanie funkcji ograniczania przepływności jest określony za pomocą ustawień pliku konfiguracji usługi.  
  
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
  
 Jeśli składnik jest udostępniany jako usługa sieci Web, odpowiedni kontrakt usługi, które będzie widoczne, a klienci będą powinny być zgodne, jest następujący:  
  
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
>  IID częścią początkowej przestrzeni nazw kontraktu.  
  
 Aplikacje klienckie, które używają tej usługi musi być zgodna z niniejszej Umowy oraz za pomocą powiązania, która jest zgodna z długością zawartą w konfiguracji aplikacji.  
  
 Poniższy przykładowy kod przedstawia domyślny plik konfiguracji. Usługi sieci Web Windows Communication Foundation (WCF), to jest zgodny ze schematem konfiguracji modelu usług w warstwie standardowa i można je edytować w taki sam sposób jak inne pliki konfiguracji usługi WCF.  
  
 Modyfikacje Typowa zamieści:  
  
- Zmienianie adresu punktu końcowego z domyślnego formularza ApplicationName/ComponentName/InterfaceName do bardziej użytecznej postaci.  
  
- Modyfikowanie przestrzeni nazw usługi z domyślnego `http://tempuri.org/InterfaceID` formularz, aby lepiej dopasowane formularza.  
  
- Zmiana punktu końcowego, aby użyć powiązania innego transportu.  
  
     W modelu COM +-hostowanej przypadkach transportu do potoków nazwanych jest używany domyślnie, ale zamiast tego można transportu wyłączyć maszyny, podobnie jak protokół TCP.  
  
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
