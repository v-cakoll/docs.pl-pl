---
title: Zabezpieczanie transportu za pomocą anonimowego klienta
description: Zapoznaj się z tym scenariuszem WCF, który korzysta z zabezpieczeń transportu do uwierzytelniania serwera przy użyciu certyfikatu, który ufa klientowi. Klient nie jest uwierzytelniony.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 08cfb8c1a5581f17a251224430018764bed80b0f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245014"
---
# <a name="transport-security-with-an-anonymous-client"></a>Zabezpieczanie transportu za pomocą anonimowego klienta

W tym scenariuszu Windows Communication Foundation (WCF) do zapewnienia poufności i integralności jest stosowany protokół HTTPS (Transport Security). Serwer musi być uwierzytelniany przy użyciu certyfikatu SSL (SSL), a klienci muszą ufać certyfikatowi serwera. Klient nie jest uwierzytelniany przez żaden mechanizm i jest w tym przypadku anonimowy.

Aby uzyskać przykładową aplikację, zobacz [WS Transport Security](../samples/ws-transport-security.md). Aby uzyskać więcej informacji na temat zabezpieczeń transportu, zobacz [Omówienie zabezpieczeń transportu](transport-security-overview.md).

Aby uzyskać więcej informacji na temat korzystania z certyfikatu z usługą, zobacz [Praca z certyfikatami](working-with-certificates.md) i [instrukcje: Konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).

![Korzystanie z zabezpieczeń transportu z anonimowym klientem](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|Charakterystyka|Opis|
|--------------------|-----------------|
|Tryb zabezpieczeń|Transport|
|Współdziałanie|Z istniejącymi usługami i klientami sieci Web|
|Uwierzytelnianie (serwer)<br /><br /> Uwierzytelnianie (klient)|Tak<br /><br /> Poziom aplikacji (brak obsługi WCF)|
|Integralność|Tak|
|Poufność|Tak|
|Transport|HTTPS|
|Wiązanie|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a>Usługa

Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania. Wykonaj jedną z następujących czynności:

- Tworzenie usługi autonomicznej przy użyciu kodu bez konfiguracji.

- Utwórz usługę przy użyciu podanej konfiguracji, ale nie Definiuj żadnych punktów końcowych.

### <a name="code"></a>Kod

Poniższy kod pokazuje, jak utworzyć punkt końcowy przy użyciu zabezpieczeń transportu:

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a>Konfiguracja

Poniższy kod konfiguruje ten sam punkt końcowy przy użyciu konfiguracji. Klient nie jest uwierzytelniany przez żaden mechanizm i dlatego jest anonimowy.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="ServiceModel.Calculator">
        <endpoint address="https://localhost/Calculator"
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

Poniższy kod i konfiguracja są przeznaczone do niezależnego uruchamiania. Wykonaj jedną z następujących czynności:

- Utwórz klienta autonomicznego przy użyciu kodu (i kodu klienta).

- Utwórz klienta, który nie definiuje żadnych adresów punktów końcowych. Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument. Przykład:

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a>Kod

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a>Konfiguracja

W celu skonfigurowania usługi można użyć następującej konfiguracji zamiast kodu.

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

- [Przegląd zabezpieczeń](security-overview.md)
- [Zabezpieczenia transportu WS](../samples/ws-transport-security.md)
- [Przegląd zabezpieczeń transportu](transport-security-overview.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
