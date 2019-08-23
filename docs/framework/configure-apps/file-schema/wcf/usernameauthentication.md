---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 399158632d5c17a35ded02691ba35a231e6cdc6e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940532"
---
# <a name="usernameauthentication"></a>\<userNameAuthentication>
Określa poświadczenia usługi na podstawie nazwy użytkownika i hasła.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
\<serviceCredentials>  
\<userNameAuthentication>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|A <xref:System.TimeSpan> , która określa maksymalny czas buforowania tokenu. Wartość domyślna to 00:15:00.|  
|`cacheLogonTokens`|Wartość logiczna określająca, czy tokeny logowania są buforowane. Wartość domyślna to `false`.|  
|`customUserNamePasswordValidatorType`|Ciąg określający typ niestandardowego modułu weryfikacji hasła użytkownika, który ma być używany. Wartość domyślna to pusty ciąg.|  
|`includeWindowsGroups`|Wartość logiczna określająca, czy grupy systemu Windows znajdują się w kontekście zabezpieczeń. Wartość domyślna to `true`.<br /><br /> Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ skutkuje rozwinięciem całej grupy. Ustaw tę właściwość na `false` , jeśli nie ma potrzeby ustanawiania listy grup, do których należy użytkownik.|  
|`maxCacheLogonTokens`|Liczba całkowita określająca maksymalną liczbę tokenów logowania do buforowania. Ta wartość powinna być większa niż zero. Wartość domyślna to 128.|  
|`membershipProviderName`|Gdy atrybut powiązania jest ustawiony na `username`, nazwa użytkownika jest mapowana na konta systemu Windows. `clientCredentialType` Można przesłonić to zachowanie przy użyciu tego atrybutu, który jest ciągiem zawierającym nazwę <xref:System.Web.Security.MembershipProvider> wartości, która zapewnia odpowiedni mechanizm walidacji hasła.|  
|`userNamePasswordValidationMode`|Określa sposób sprawdzania poprawności hasła nazwy użytkownika. Prawidłowe wartości to:<br /><br /> — System Windows<br />- MembershipProvider<br />-Niestandardowe<br /><br /> Wartość domyślna to Windows. Ten atrybut jest typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi oraz ustawienia powiązane z walidacją poświadczeń klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli żaden z powiązań używanych przez usługę nie jest skonfigurowany do uwierzytelniania opartego na nazwie użytkownika/hasła, atrybuty tego elementu są ignorowane. Należą `customUserNamePasswordValidatorType`do nich `includeWindowsGroups`, `membershipProviderName`,, `userNamePasswordValidationMode`i.  
  
 Jeśli żaden z powiązań używanych przez usługę nie jest skonfigurowany do korzystania z uwierzytelniania systemu Windows dla nazwy użytkownika/hasła, ustawienia związane z buforowaniem tokenów logowania są ignorowane. Należą do `cacheLogonTokenLifetime`nich, `cacheLogonTokens`i. `maxCacheLogonTokens`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
