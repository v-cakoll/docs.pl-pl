---
title: 'Instrukcje: konfigurowanie ustawień usługi COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: 3fb4b31038845d223248e72d32b3e7413f2aef63
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597179"
---
# <a name="how-to-configure-com-service-settings"></a>Instrukcje: konfigurowanie ustawień usługi COM+
Gdy interfejs aplikacji zostanie dodany lub usunięty przy użyciu narzędzia konfiguracji usługi COM+, konfiguracja usługi sieci Web jest aktualizowana w pliku konfiguracyjnym aplikacji. W trybie hostowanym modelu COM+ plik Application. config jest umieszczany w katalogu głównym aplikacji (domyślnie są to aplikacje%PROGRAMFILES%\ComPlus \\ {AppID}). W każdym z trybów hostowanych w sieci Web plik Web. config znajduje się w określonym katalogu wirtualnym.  
  
> [!NOTE]
> Podpisywanie komunikatów należy używać do ochrony przed manipulacją komunikatów między klientem a serwerem. Ponadto w celu ochrony przed ujawnieniem informacji z komunikatów między klientem a serwerem należy użyć szyfrowania z warstwy komunikatów lub transportu. Podobnie jak w przypadku usług Windows Communication Foundation (WCF), należy użyć ograniczania przepustowości, aby ograniczyć liczbę współbieżnych wywołań, połączeń, wystąpień i oczekujących operacji. Pozwala to zapobiec nadmiernemu zużyciu zasobów. Zachowanie ograniczania jest określone za poorednictwem ustawień pliku konfiguracji usługi.  
  
## <a name="example"></a>Przykład  
 Rozważmy składnik implementujący następujący interfejs:  
  
```csharp
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 Jeśli składnik jest udostępniany jako usługa sieci Web, odpowiadający mu kontrakt usługi, który jest udostępniany, a klienci muszą spełniać następujące warunki:  
  
```csharp
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
> Identyfikator IID stanowi część początkowej przestrzeni nazw dla kontraktu.  
  
 Aplikacje klienckie korzystające z tej usługi muszą być zgodne z tym kontraktem wraz z użyciem powiązania, które jest zgodne z określonym w konfiguracji aplikacji.  
  
 Poniższy przykład kodu pokazuje domyślny plik konfiguracji. Jest to usługa sieci Web programu Windows Communication Foundation (WCF), która jest zgodna ze schematem konfiguracji standardowego modelu usług i można ją edytować w taki sam sposób, jak w przypadku innych plików konfiguracji usług WCF.  
  
 Typowe modyfikacje obejmują:  
  
- Zmiana adresu punktu końcowego z domyślnego typu ApplicationName/ComponentName/InterfaceName na bardziej użyteczny formularz.  
  
- Modyfikowanie przestrzeni nazw usługi z poziomu `http://tempuri.org/InterfaceID` formularza domyślnego na bardziej istotny.  
  
- Zmiana punktu końcowego w taki sposób, aby używał innego powiązania transportowego.  
  
     W przypadku aplikacji w przypadku modelu COM+ jest używana domyślnie transport potoków nazwanych, ale zamiast tego można użyć transportu poza komputerem.  
  
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

- [Integrowanie z aplikacjami COM+](integrating-with-com-plus-applications.md)
