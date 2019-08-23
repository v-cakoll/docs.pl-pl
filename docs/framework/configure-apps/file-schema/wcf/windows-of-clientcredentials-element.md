---
title: <windows><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: e9f0ed9879cc42ea25b83e6b626139a40a593112
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940306"
---
# <a name="windows-of-clientcredentials-element"></a>\<> systemu Windows \<obiektu ClientCredentials >
Określa ustawienia poświadczeń systemu Windows, które mają być używane do reprezentowania klienta.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<endpointBehaviors>  
\<> zachowania  
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
|`allowedImpersonationLevel`|Ustawia preferencje personifikacji, które klient komunikuje się z serwerem. Tryb personifikacji wybierany przez klienta nie jest wymuszany na serwerze. Prawidłowe wartości to:<br /><br /> Identyfikatora Serwer może uzyskać tożsamość i uprawnienia klienta, ale nie może personifikować klienta.<br />Chodzi Serwer może personifikować kontekst zabezpieczeń klienta w systemie lokalnym.<br />Wierz Serwer może personifikować kontekst zabezpieczeń klienta w systemach zdalnych.<br />Anonimowe Serwer nie może personifikować lub zidentyfikować klienta.<br />Dawaj Nie przypisano poziomu personifikacji.<br /><br /> Wartość domyślna to Identification. Ten atrybut jest typu <xref:System.Security.Principal.TokenImpersonationLevel>.|  
|`allowNtlm`|Ustawienie tej właściwości `true` umożliwia uwierzytelnianie w przypadku, gdy protokół Kerberos jest niedostępny.<br /><br /> Ustawienie tej właściwości `false` powoduje, że Windows Communication Foundation (WCF), aby najlepszym wysiłku zgłosić wyjątek, jeśli jest używany protokół NTLM. Należy pamiętać, że ustawienie tej `false` właściwości na nie zapobiega wysyłaniu poświadczeń NTLM za pośrednictwem sieci.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Określa poświadczenia używane do uwierzytelniania klienta w usłudze.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [Zabezpieczanie klientów](../../../wcf/securing-clients.md)
- [Praca z certyfikatami](../../../wcf/feature-details/working-with-certificates.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
