---
title: <windows> z <clientCredentials> — Element
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: b5e92745b9e39534d2a0bc35504c2dbc8346d2ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221023"
---
# <a name="windows-of-clientcredentials-element"></a>\<Windows > z \<clientCredentials > Element
Określa ustawienia dla poświadczenia Windows do użycia do reprezentacji klienta.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<endpointBehaviors>  
\<zachowanie >  
\<clientCredentials>  
\<windows>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|Ustawia preferencje personifikacji, który klient komunikuje się z serwerem. Tryb personifikacji, który klient wybiera nie są wymuszane na serwerze. Prawidłowe wartości są następujące:<br /><br /> — Identyfikator: Serwer można uzyskać tożsamości i uprawnień klienta, ale nie można spersonifikować klienta.<br />-Personifikacji: Serwer może personifikować klienta kontekstu zabezpieczeń w systemie lokalnym.<br />-Delegowania: Serwer może personifikować klienta kontekstu zabezpieczeń w systemach zdalnych.<br />-Anonimowe: Serwer nie może spersonifikować lub identyfikacji klienta.<br />-Brak: Nie przypisano poziom personifikacji.<br /><br /> Wartość domyślna to identyfikator. Ten atrybut jest typu <xref:System.Security.Principal.TokenImpersonationLevel>.|  
|`allowNtlm`|Ustawienie tej właściwości na `true` umożliwia uwierzytelnianie do poziomu starszej wersji NTLM, jeżeli protokół Kerberos nie jest dostępna.<br /><br /> Ustawienie tej właściwości na `false` powoduje, że Windows Communication Foundation (WCF) umożliwiają staranności do zgłoszenia wyjątku, jeśli używane jest uwierzytelnianie NTLM. Należy pamiętać, że ustawienie tej właściwości na `false` może uniemożliwia poświadczeń NTLM są przesyłane przez sieć.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Określa poświadczenia używane do uwierzytelniania klienta do usługi.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [Zabezpieczanie klientów](../../../../../docs/framework/wcf/securing-clients.md)
- [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
