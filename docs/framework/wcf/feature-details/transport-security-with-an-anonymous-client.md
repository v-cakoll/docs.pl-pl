---
title: "Zabezpieczanie transportu za pomocą anonimowego klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 97a3c9c618fc7d6c96deba0b72e25ef36c5785e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transport-security-with-an-anonymous-client"></a>Zabezpieczanie transportu za pomocą anonimowego klienta
To [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] scenariuszu zapewnienie poufności i integralności zabezpieczeń transportowych (HTTPS). Serwer musi zostać uwierzytelniony przy użyciu certyfikatu protokołu Secure Sockets Layer (SSL), a klienci muszą ufać certyfikatu serwera. Klient nie został uwierzytelniony przy użyciu dowolnego mechanizmu i jest anonimowy.  
  
 Przykładową aplikację, zobacz [zabezpieczenia transportu WS](../../../../docs/framework/wcf/samples/ws-transport-security.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]zabezpieczenia transportu, zobacz [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]za pomocą certyfikatu usługi, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) i [porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
 ![Za pomocą zabezpieczeń transportu za pomocą anonimowego klienta](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931-0cfb-4aaa-9272-91d652b85d8d")  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Transportu|  
|Współdziałanie|Z istniejącymi usługami sieci Web i klientami|  
|Uwierzytelnianie (serwer)<br /><br /> Uwierzytelnianie (klient)|Tak<br /><br /> Poziom aplikacji (nie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje)|  
|Integralność|Tak|  
|Poufność|Tak|  
|Transportu|HTTPS|  
|Powiązanie|<<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>|  
  
## <a name="service"></a>Usługa  
 Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
-   Tworzenie przy użyciu kodu z konfiguracji autonomicznej usługi.  
  
-   Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.  
  
### <a name="code"></a>Kod  
 Poniższy kod przedstawia sposób tworzenia punktu końcowego za pomocą zabezpieczeń transportu:  
  
 [!code-csharp[c_SecurityScenarios#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
 [!code-vb[c_SecurityScenarios#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]  
  
### <a name="configuration"></a>Konfiguracja  
 Poniższy kod konfiguruje tego samego punktu końcowego za pomocą konfiguracji. Klient nie został uwierzytelniony przy użyciu dowolnego mechanizmu i dlatego jest anonimowy.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
 Następujący kod i konfiguracja są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
-   Utwórz autonomiczny klienta przy użyciu kodu (i kod klienta).  
  
-   Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych. W zamian użyj Konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument. Na przykład:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_SecurityScenarios#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
 [!code-vb[c_SecurityScenarios#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]  
  
### <a name="configuration"></a>Konfiguracja  
 Następującej konfiguracji można zamiast kodu do skonfigurowania usługi.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Zabezpieczenia transportu WS](../../../../docs/framework/wcf/samples/ws-transport-security.md)  
 [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
