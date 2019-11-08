---
title: <transport> dla <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732737"
---
# <a name="transport-of-wshttpbinding"></a>\<Transport > \<wsHttpBinding >

Definiuje ustawienia uwierzytelniania dla transportu HTTP.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<WSHttpBinding**](wshttpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpieczeń**](security-of-wshttpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**  

## <a name="syntax"></a>Składnia

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a>Typ

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`clientCredentialType`|Określa poświadczenie używane do uwierzytelniania klienta w usłudze. Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.|
|`proxyCredentialType`|Określa poświadczenie używane do uwierzytelniania klienta programu na serwerze proxy domeny. Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.|
|`realm`|Ciąg określający obszar uwierzytelniania dla uwierzytelniania szyfrowanego lub podstawowego. Wartość domyślna to pusty ciąg.<br /><br /> Obszar uwierzytelniania określa co najmniej nazwę hosta, który wykonuje uwierzytelnianie. Można również określić kolekcję użytkowników, którzy mają dostęp. Użytkownik może wysyłać zapytania do obszaru uwierzytelniania, aby upewnić się, że można użyć jednej z kilku nazw użytkowników i haseł.|
|`policyEnforcement`|To Wyliczenie określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> należy wymusić.<br /><br /> 1. nigdy — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).<br />2. WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochronę rozszerzoną.<br />3. zawsze — zasady są zawsze wymuszane. Klienci, którzy nie obsługują rozszerzonej ochrony, nie będą uwierzytelniani.|

## <a name="clientcredentialtype-attribute"></a>clientCredentialtype — atrybut

|Wartość|Opis|
|-----------|-----------------|
|`None`|Zabezpieczenia są wyłączone.|
|`Basic`|Używa uwierzytelniania podstawowego.|
|`Digest`|Używa uwierzytelniania szyfrowanego.|
|`Ntlm`|Używa uwierzytelniania NTLM jako rezerwy z domeną systemu Windows.|
|`Windows`|Używa zintegrowanego uwierzytelniania systemu Windows.|
|`Certificate`|Uwierzytelnia klienta za pomocą certyfikatów X. 509.|

## <a name="proxycredentialtype-attribute"></a>proxyCredentialType — atrybut

|Wartość|Opis|
|-----------|-----------------|
|`None`|Zabezpieczenia są wyłączone.|
|`Basic`|Używa uwierzytelniania podstawowego.|
|`Digest`|Używa uwierzytelniania szyfrowanego.|
|`Ntlm`|Używa protokołu NTLM jako rezerwy z domeną systemu Windows.|
|`Windows`|Używa zintegrowanego uwierzytelniania systemu Windows.|
|`Certificate`|Uwierzytelnia klienta za pomocą certyfikatów X. 509.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[> zabezpieczeń \<](security-of-wshttpbinding.md)|Reprezentuje możliwości zabezpieczeń [\<> WSHttpBinding](wshttpbinding.md).|

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [> powiązań \<](bindings.md)
