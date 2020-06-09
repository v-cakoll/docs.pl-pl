---
title: Niezabezpieczony klient internetowy i usługa
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: 0b02d1efc98f02390555861871d280f9800ced1e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598882"
---
# <a name="internet-unsecured-client-and-service"></a>Niezabezpieczony klient internetowy i usługa
Na poniższej ilustracji przedstawiono przykład publicznego, niezabezpieczonego Windows Communication Foundation (WCF) i usługi:  
  
 ![Zrzut ekranu przedstawiający niezabezpieczony scenariusz internetowy](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|Charakterystyka|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Brak|  
|Transport|HTTP|  
|Wiązanie|<xref:System.ServiceModel.BasicHttpBinding>w kodzie lub w [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) elemencie konfiguracji.|  
|Współdziałanie|Z istniejącymi usługami i klientami usług sieci Web|  
|Authentication|Brak|  
|Integralność|Brak|  
|Poufność|Brak|  
  
## <a name="service"></a>Usługa  
 Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania. Wykonaj jedną z następujących czynności:  
  
- Tworzenie usługi autonomicznej przy użyciu kodu bez konfiguracji.  
  
- Utwórz usługę przy użyciu podanej konfiguracji, ale nie Definiuj żadnych punktów końcowych.  
  
### <a name="code"></a>Kod  
 Poniższy kod pokazuje, jak utworzyć punkt końcowy bez zabezpieczeń. Domyślnie <xref:System.ServiceModel.BasicHttpBinding> ma tryb zabezpieczeń ustawiony na <xref:System.ServiceModel.BasicHttpSecurityMode.None> .  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a>Konfiguracja usługi  
 Poniższy kod konfiguruje ten sam punkt końcowy przy użyciu konfiguracji.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="basicHttpBinding"  
                  bindingConfiguration="Basic_Unsecured"
                  name="BasicHttp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="Basic_Unsecured" />  
      </basicHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
 Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania. Wykonaj jedną z następujących czynności:  
  
- Utwórz klienta autonomicznego przy użyciu kodu (i kodu klienta).  
  
- Utwórz klienta, który nie definiuje żadnych adresów punktów końcowych. Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument. Przykład:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Poniższy kod przedstawia podstawowy klient WCF, który uzyskuje dostęp do niezabezpieczonego punktu końcowego.  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a>Konfiguracja klienta  
 Poniższy kod konfiguruje klienta.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="BasicHttpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator/Unsecured"  
          binding="basicHttpBinding"
          bindingConfiguration="BasicHttpBinding_ICalculator"  
          contract="ICalculator"
          name="BasicHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Typowe scenariusze zabezpieczeń](common-security-scenarios.md)
- [Przegląd zabezpieczeń](security-overview.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
