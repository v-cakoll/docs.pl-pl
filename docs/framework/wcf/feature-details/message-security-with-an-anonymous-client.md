---
title: Zabezpieczenia komunikatów z anonimowym klientem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 058163c96bba036c3183695bf986b4d0424271ac
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595222"
---
# <a name="message-security-with-an-anonymous-client"></a>Zabezpieczenia komunikatów z anonimowym klientem

W poniższym scenariuszu przedstawiono klienta i usługę zabezpieczone przez Windows Communication Foundation (WCF) zabezpieczenia komunikatów. Celem projektowania jest korzystanie z zabezpieczeń komunikatów zamiast zabezpieczeń transportu, dzięki czemu w przyszłości może obsługiwać bogatszy model oparty na oświadczeniach. Aby uzyskać więcej informacji o korzystaniu z rozbudowanych oświadczeń do autoryzacji, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](managing-claims-and-authorization-with-the-identity-model.md).

Aby zapoznać się z przykładową aplikacją, zobacz [zabezpieczenia wiadomości anonimowe](../samples/message-security-anonymous.md).

![Zabezpieczenia komunikatów z anonimowym klientem](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")

|Charakterystyka|Opis|
|--------------------|-----------------|
|Tryb zabezpieczeń|Komunikat|
|Współdziałanie|Tylko WCF|
|Uwierzytelnianie (serwer)|Początkowe negocjowanie wymaga uwierzytelniania serwera, ale nie uwierzytelniania klienta|
|Uwierzytelnianie (klient)|Brak|
|Integralność|Tak, przy użyciu kontekstu zabezpieczeń udostępnionych|
|Poufność|Tak, przy użyciu kontekstu zabezpieczeń udostępnionych|
|Transport|HTTP|

## <a name="service"></a>Usługa

Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania. Wykonaj jedną z następujących czynności:

- Tworzenie usługi autonomicznej przy użyciu kodu bez konfiguracji.

- Utwórz usługę przy użyciu podanej konfiguracji, ale nie Definiuj żadnych punktów końcowych.

### <a name="code"></a>Kod

Poniższy kod przedstawia sposób tworzenia punktu końcowego usługi, który korzysta z zabezpieczeń komunikatów.

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a>Konfigurowanie

Można użyć poniższej konfiguracji zamiast kodu. Element zachowania usługi służy do określania certyfikatu, który jest używany do uwierzytelniania usługi dla klienta. Element Service musi określać zachowanie przy użyciu `behaviorConfiguration` atrybutu. Element Binding określa, że typ poświadczeń klienta to `None` , co umożliwia anonimowym klientom korzystanie z usługi.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
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

Poniższy kod tworzy wystąpienie klienta. Powiązanie używa zabezpieczeń trybu komunikatów, a typ poświadczeń klienta ma wartość none.

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a>Konfigurowanie

Poniższy kod konfiguruje klienta.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://machineName/Calculator"
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_ICalculator"
        contract="ICalculator"
        name="WSHttpBinding_ICalculator">
        <identity>
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>Zobacz też

- [Przegląd zabezpieczeń](security-overview.md)
- [Rozproszone zabezpieczenia aplikacji](distributed-application-security.md)
- [Zabezpieczenia komunikatów z anonimowością](../samples/message-security-anonymous.md)
- [Uwierzytelnianie i tożsamość usług](service-identity-and-authentication.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
