---
title: Zabezpieczanie transportu za pomocą anonimowego klienta - usługi WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: aac3b2ac6cfcca137bddaefafd290e744ee991eb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637437"
---
# <a name="transport-security-with-an-anonymous-client"></a>Zabezpieczanie transportu za pomocą anonimowego klienta

W tym scenariuszu usług Windows Communication Foundation (WCF) używane zabezpieczeń transportowych (HTTPS), aby upewnić się, poufności i integralności. Serwer musi zostać uwierzytelniony przy użyciu certyfikatu Secure Sockets Layer (SSL), a klienci muszą ufać certyfikatowi serwera. Klient nie został uwierzytelniony przy użyciu dowolnego mechanizmu i jest zatem anonimowe.

Dla przykładowej aplikacji, zobacz [zabezpieczenia transportu WS](../samples/ws-transport-security.md). Aby uzyskać więcej informacji na temat zabezpieczeń transportu zobacz [Przegląd zabezpieczeń transportu](transport-security-overview.md).

Aby uzyskać więcej informacji na temat używania certyfikatu z usługą, zobacz [Working with Certificates](working-with-certificates.md) i [jak: Konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).

![Za pomocą zabezpieczeń transportu z anonimowym klientem](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|Cechy|Opis|
|--------------------|-----------------|
|Tryb zabezpieczeń|Transport|
|Współdziałanie|Przy użyciu istniejących usług sieci Web i klientów|
|Uwierzytelnianie (serwer)<br /><br /> Uwierzytelnianie (klient)|Tak<br /><br /> Poziom aplikacji (bez obsługi WCF)|
|Integralność|Tak|
|Poufność|Tak|
|Transport|HTTPS|
|Wiązanie|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a>Usługa

Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:

- Tworzenie autonomicznego usługi przy użyciu kodu bez konfiguracji.

- Tworzenie usługi przy użyciu wprowadzonej konfiguracji, ale nie definiują żadnych punktów końcowych.

### <a name="code"></a>Kod

Poniższy kod przedstawia sposób tworzenia punktu końcowego za pomocą zabezpieczeń transportu:

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a>Konfiguracja

Poniższy kod ustawia ten sam punkt końcowy, za pomocą konfiguracji. Klient nie został uwierzytelniony przy użyciu dowolnego mechanizmu i w związku z tym jest anonimowy.

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

Następujący kod i konfiguracji są przeznaczone do uruchamiania niezależnie. Wykonaj jedną z następujących czynności:

- Tworzenie klienta autonomicznego przy użyciu kodu (i kodu klienta).

- Tworzenie klienta, który nie definiuje żadnych adresy punktów końcowych. Zamiast tego należy użyć konstruktora klienta, który przyjmuje nazwę konfiguracji jako argument. Na przykład:

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a>Kod

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a>Konfiguracja

Następująca konfiguracja może służyć zamiast kodu do konfiguracji obsługiwanej usługi.

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

## <a name="see-also"></a>Zobacz także

- [Przegląd zabezpieczeń](security-overview.md)
- [Zabezpieczenia transportu WS](../samples/ws-transport-security.md)
- [Przegląd zabezpieczeń transportu](transport-security-overview.md)
- [Model zabezpieczeń dla systemu Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
