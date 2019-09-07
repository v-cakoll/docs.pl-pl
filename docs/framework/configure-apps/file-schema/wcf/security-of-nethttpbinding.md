---
title: <security> dla <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 890cee3271c410a921b3a88f78d0705ba8718252
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399857"
---
# <a name="security-of-nethttpbinding"></a>\<> \<zabezpieczeń > protokołu HttpBinding

Definiuje możliwości [ \<zabezpieczeń protokołu HttpBinding >](nethttpbinding.md).

[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> protokołu HttpBinding**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpieczeń**  

## <a name="syntax"></a>Składnia

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|tryb|Opcjonalna. Określa typ używanego zabezpieczenia. Wartość domyślna to `None`. Ten atrybut jest typu <xref:System.ServiceModel.BasicHttpSecurityMode>.|

## <a name="mode-attribute"></a>atrybut Mode

|Wartość|Opis|
|-----------|-----------------|
|Brak|-Komunikaty nie są zabezpieczane podczas transferu.|
|Transportu|Zabezpieczenia są udostępniane przy użyciu protokołu HTTPS. Komunikaty protokołu SOAP są zabezpieczone przy użyciu protokołu HTTPS. Usługa jest uwierzytelniana na kliencie przy użyciu certyfikatu X. 509 usługi. Klient jest uwierzytelniany przy użyciu dostarczonego obiekt ClientCredentialtype.|
|Message|Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP. Domyślnie treść jest zaszyfrowana i podpisana. W przypadku tego powiązania system wymaga, aby certyfikat serwera został dostarczony do klienta poza pasmem. Jedyna prawidłowa `ClientCredentialType` dla tego powiązania to `Certificate`.|
|TransportWithMessageCredential|Integralność, poufność i uwierzytelnianie serwera są udostępniane przez zabezpieczenia transportu. Uwierzytelnianie klienta jest zapewniane przez zabezpieczenia komunikatów protokołu SOAP. Ten tryb jest istotny, gdy użytkownik jest uwierzytelniany przy użyciu nazwy użytkownika/hasła i istnieje wdrożenie HTTP na potrzeby zabezpieczania transferu komunikatów.|
|TransportCredentialOnly|Ten tryb nie zapewnia integralności i poufności komunikatów. Zapewnia uwierzytelnianie klienta oparte na protokole HTTP. Ten tryb powinien być używany z zachowaniem ostrożności. Powinna być używana w środowiskach, w których zabezpieczenia transportu są dostarczane przy użyciu innych metod (takich jak IPSec) i tylko uwierzytelnianie klienta jest udostępniane przez infrastrukturę WCF.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<> transportu](transport-of-nethttpbinding.md)|Definiuje ustawienia zabezpieczeń transportu dla podstawowej usługi HTTP. Ten element odnosi się <xref:System.ServiceModel.HttpTransportSecurity>do.|
|[\<message>](message-of-nethttpbinding.md)|Definiuje ustawienia zabezpieczeń wiadomości dla podstawowej usługi HTTP. Ten element odnosi się <xref:System.ServiceModel.BasicHttpMessageSecurity>do.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|powiązanie|Element Binding elementu [ \<BasicHttpBinding >](basichttpbinding.md).|

## <a name="remarks"></a>Uwagi

 Domyślnie komunikat protokołu SOAP nie jest zabezpieczony i klient nie jest uwierzytelniany. Ten element umożliwia skonfigurowanie dodatkowych ustawień zabezpieczeń dla `netHttpBinding` elementu.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Wybieranie typu poświadczeń](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> powiązania](../../../misc/binding.md)
