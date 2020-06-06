---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: c6183a8d27d56c7199b815ccb31b06f983a51b33
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398400"
---
# \<messageSenderAuthentication>
Określa ustawienia uwierzytelniania dla certyfikatu równorzędnego używanego przez nadawcę wiadomości.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`certificateValidationMode`|Opcjonalne Wyliczenie. Określa jeden z pięciu trybów używanych do walidacji poświadczeń. Ten atrybut jest typu <xref:System.ServiceModel.Security.X509CertificateValidationMode> . Jeśli jest ustawiona na `Custom` , `customCertificateValidator` należy również podać wartość.|  
|`customCertificateValidatorType`|Opcjonalny ciąg. Określa typ i zestaw używany do walidacji typu niestandardowego. Ten atrybut musi być ustawiony `certificateValidationMode` , gdy jest ustawiony na `Custom` . Ten atrybut jest typu <xref:System.IdentityModel.Selectors.X509CertificateValidator> . Windows Communication Foundation (WCF) udostępnia domyślny moduł sprawdzania poprawności certyfikatu równorzędnego, który weryfikuje certyfikat równorzędny w magazynie zaufanych osób. Sprawdza również, czy certyfikat jest łańcuchem do prawidłowego katalogu głównego. Możesz zaimplementować niestandardowy moduł sprawdzania poprawności, aby określić inne zachowanie i użyć tego atrybutu, aby wskazać niestandardowy moduł sprawdzania poprawności.|  
|`revocationMode`|Opcjonalne Wyliczenie. Określa tryb odwoływania certyfikatu. Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> . System sprawdza, czy certyfikat równorzędny nie został odwołany, sprawdzając go na liście odwołanych certyfikatów. Ten test można przeprowadzić przez sprawdzenie w trybie online lub w odniesieniu do buforowanej listy odwołania. Sprawdzanie odwołania można wyłączyć, ustawiając ten atrybut na NOCHECK.|  
|`trustedStoreLocation`|Opcjonalne Wyliczenie. Określa lokalizację zaufanego magazynu, w której certyfikat równorzędny jest sprawdzany przez system zabezpieczeń WCF. Ten atrybut jest typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation> .|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|Określa bieżące poświadczenia dla węzła równorzędnego.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element musi być skonfigurowany, jeśli wybrano opcję Uwierzytelnianie wiadomości. W przypadku kanałów wyjściowych każdy komunikat jest podpisywany przy użyciu certyfikatu dostarczonego przez [\<certificate>](certificate-element.md) . Wszystkie komunikaty, przed dostarczeniem do aplikacji, są sprawdzane pod kątem poświadczeń komunikatów przy użyciu modułu walidacji określonego przez `customCertificateValidatorType` atrybut tego elementu. Moduł sprawdzania poprawności może zaakceptować lub odrzucić poświadczenie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md)
- [Sieci równorzędne](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Uwierzytelnianie komunikatów kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Uwierzytelnianie niestandardowe kanału równorzędnego](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Zabezpieczanie aplikacji kanałów równorzędnych](../../../wcf/feature-details/securing-peer-channel-applications.md)
