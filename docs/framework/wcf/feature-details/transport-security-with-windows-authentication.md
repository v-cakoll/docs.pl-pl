---
title: Zabezpieczenia transportu z uwierzytelnianiem systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 96fce3cb56cf328e0fbb589113e3ac24519de557
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125450"
---
# <a name="transport-security-with-windows-authentication"></a>Zabezpieczenia transportu z uwierzytelnianiem systemu Windows
Następujący scenariusz pokazuje klienta usługi Windows Communication Foundation (WCF) i usług zabezpieczonych przez usługę Windows security. Aby uzyskać więcej informacji na temat programowania, zobacz [jak: Zabezpieczanie usługi za pomocą poświadczeń Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
 Intranet usługi sieci Web Wyświetla informacje o zasobów ludzkich. Klient to aplikacja formularza Windows. Aplikacja jest wdrażana w domenie za pomocą kontrolera Kerberos zabezpieczanie domeny.  
  
 ![Zabezpieczenia transportu z uwierzytelnianiem Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|Cechy|Opis|  
|--------------------|-----------------|  
|Tryb zabezpieczeń|Transport|  
|Współdziałanie|Tylko usługi WCF|  
|Uwierzytelnianie (serwer)<br /><br /> Uwierzytelnianie (klient)|Tak (za pomocą zintegrowanego uwierzytelniania Windows)<br /><br /> Tak (za pomocą zintegrowanego uwierzytelniania Windows)|  
|Integralność|Tak|  
|Poufność|Tak|  
|Transport|NET.TCP|  
|Wiązanie|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a>Usługa  
 Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
-   Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.  
  
-   Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.  
  
### <a name="code"></a>Kod  
 Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, która używa zabezpieczenia Windows.  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a>Konfiguracja  
 Następująca konfiguracja może służyć zamiast kodu do konfigurowania punktu końcowego usługi:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"   
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Klient  
 Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:  
  
-   Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).  
  
-   Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych. Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument. Na przykład:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Poniższy kod tworzy klienta. Powiązanie jest skonfigurowane za pomocą transportu tryb zabezpieczeń transportu TCP za pomocą typu poświadczeń klienta równa Windows.  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a>Konfiguracja  
 Następująca konfiguracja może służyć zamiast kodu do tworzenia klienta.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"   
                binding="netTcpBinding"            
                bindingConfiguration="NetTcpBinding_ICalculator"   
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
