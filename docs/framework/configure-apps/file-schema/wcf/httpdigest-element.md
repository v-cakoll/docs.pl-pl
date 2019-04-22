---
title: <httpDigest>, element
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 914711e4d6c3dbb1ccc741af1b3abd6b8de716a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165324"
---
# <a name="httpdigest-element"></a>\<httpDigest> Element
Określa szyfrowany typ poświadczenia używany podczas uwierzytelniania klienta do usługi.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<endpointBehaviors>  
\<zachowanie >  
\<clientCredentials>  
\<httpDigest>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`impersonationLevel`|Ustawia preferencje personifikacji, który klient komunikuje się z serwerem. Tryb personifikacji, który klient wybiera nie są wymuszane na serwerze. Prawidłowe wartości są następujące:<br /><br /> — Identyfikator: Serwer można uzyskać tożsamości i uprawnień klienta, ale nie można spersonifikować klienta.<br />-Personifikacji: Serwer może personifikować klienta kontekstu zabezpieczeń w systemie lokalnym.<br />-Delegowania: Serwer może personifikować klienta kontekstu zabezpieczeń w systemach zdalnych.<br />-Anonimowe: Serwer nie może spersonifikować lub identyfikacji klienta.<br />-Brak: Nie przypisano poziom personifikacji.<br /><br /> Wartość domyślna to identyfikator. Ten atrybut jest typu <xref:System.Security.Principal.TokenImpersonationLevel>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Określa poświadczenia używane do uwierzytelniania klienta do usługi.|  
  
## <a name="remarks"></a>Uwagi  
 Podsumowanie jest skrót, określić przy użyciu algorytmu i zestaw danych wejściowych. Wystawca uwierzytelnienia uwierzytelnionego zgody na algorytm i wymiany danych, używane jako dane wejściowe. Klient może obliczenia skrótu i wysyłać je do usługi. Ta usługa również oblicza skrót i porównuje wartości. Dopasowanie weryfikuje klienta.  
  
 Ta funkcja wymaga włączenia w usłudze Active Directory, Windows i Internet Information Services (IIS). Aby uzyskać więcej informacji, zobacz [uwierzytelnianie szyfrowane w usługach IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Zabezpieczanie klientów](../../../../../docs/framework/wcf/securing-clients.md)
- [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
