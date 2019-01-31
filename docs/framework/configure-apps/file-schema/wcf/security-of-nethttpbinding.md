---
title: <security> z <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: f2750036aa4d3fbe41062ad041e50ff3a4be32b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283972"
---
# <a name="security-of-nethttpbinding"></a>\<Zabezpieczenia > z \<netHttpBinding >

Definiuje możliwości zabezpieczeń [ \<basicHttpBinding >](basichttpbinding.md).

\<system.ServiceModel>\
\<powiązania > \
\<netHttpBinding>\
\<Powiązanie > \
\<security>

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
|tryb|Opcjonalna. Określa typ zabezpieczeń, która jest używana. Wartość domyślna to `None`. Ten atrybut jest typu <xref:System.ServiceModel.BasicHttpSecurityMode>.|

## <a name="mode-attribute"></a>Atrybut tryb

|Wartość|Opis|
|-----------|-----------------|
|Brak|— Liczba komunikatów nie są zabezpieczane podczas przesyłania.|
|Transport|Zabezpieczenia za pomocą transportu HTTPS. Komunikaty protokołu SOAP są chronione przy użyciu protokołu HTTPS. Usługa jest uwierzytelniany przez klienta za pomocą certyfikatu X.509 usługi. Klient jest uwierzytelniany przy użyciu właściwości ClientCredentialType o wartości dostarczone.|
|Komunikat|Zabezpieczenia korzystanie z zabezpieczeń komunikatów protokołu SOAP. Domyślnie treść jest zaszyfrowany i podpisany. Dla tego powiązania systemu wymaga podania certyfikatu serwera do klienta poza pasmem. Jedyne prawidłowe `ClientCredentialType` dla tego powiązania jest `Certificate`.|
|TransportWithMessageCredential|Uwierzytelnianie integralności, poufności i serwera są dostarczane przez zabezpieczeń transportu. Uwierzytelnianie klienta znajduje się za pomocą zabezpieczeń wiadomości protokołu SOAP. Ten tryb jest istotne, po użytkownik jest uwierzytelniany przy użyciu nazwy użytkownika/hasła istniejącego wdrożenia protokołu HTTP do zabezpieczania transferu komunikatów.|
|TransportCredentialOnly|Ten tryb nie zapewnia integralność komunikatów i poufność. Zapewnia uwierzytelnianie oparte na protokole http klienta. W tym trybie, należy używać ostrożnie. Należy używać w środowiskach, gdzie zabezpieczenia transportu jest świadczona w inny sposób (takich jak IPSec), a tylko uwierzytelnianie klientów jest świadczona przez infrastrukturę usługi WCF.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|Określa ustawienia zabezpieczenia transportu podstawowa usługa HTTP. Ten element odnosi się do <xref:System.ServiceModel.HttpTransportSecurity>.|
|[\<message>](message-of-nethttpbinding.md)|Definiuje ustawienia zabezpieczeń wiadomości dla podstawowa usługa HTTP. Ten element odnosi się do <xref:System.ServiceModel.BasicHttpMessageSecurity>.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|powiązanie|Element powiązania [ \<basicHttpBinding >](basichttpbinding.md).|

## <a name="remarks"></a>Uwagi

 Domyślnie komunikat protokołu SOAP nie jest zabezpieczony, a klient nie jest uwierzytelniony. Ten element umożliwia konfigurowanie dodatkowych ustawień zabezpieczeń dla `netHttpBinding` elementu.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Wybieranie typu poświadczeń](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Powiązanie >](../../../misc/binding.md)
