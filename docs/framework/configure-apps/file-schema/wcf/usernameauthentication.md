---
title: '&lt;UserNameAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 3ade257a81e218fa123a08624123af614df84956
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150048"
---
# <a name="ltusernameauthenticationgt"></a>&lt;UserNameAuthentication&gt;
Określa poświadczenia usługi, w oparciu o nazwę użytkownika i hasło.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<userNameAuthentication >  
  
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
|`cacheLogonTokenLifetime`|Element <xref:System.TimeSpan> , który określa maksymalną długość czasu, jest buforowany token. Wartość domyślna to 00:15:00.|  
|`cacheLogonTokens`|Wartość logiczna określająca, czy tokeny logowania są buforowane. Wartość domyślna to `false`.|  
|`customUserNamePasswordValidatorType`|Ciąg, który określa typ modułu weryfikacji hasła niestandardowej nazwy użytkownika do użycia. Wartość domyślna to ciąg pusty.|  
|`includeWindowsGroups`|Wartość logiczna określająca, czy grupy Windows znajdują się w kontekście zabezpieczeń. Wartość domyślna to `true`.<br /><br /> Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ powoduje ona wystąpił błąd rozszerzania grupy pełnej. Ustaw tę właściwość na `false` Jeśli potrzebujesz nawiązać listy grup należy użytkownik.|  
|`maxCacheLogonTokens`|Liczba całkowita określająca maksymalną liczbę tokenów logowania do pamięci podręcznej. Ta wartość powinna być większa niż zero. Wartość domyślna to 128.|  
|`membershipProviderName`|Gdy `clientCredentialType` ma ustawioną wartość atrybutu powiązania `username`, nazwa użytkownika jest mapowany do konta Windows. Można zastąpić to zachowanie za pomocą tego atrybutu jest ciąg zawierający nazwę <xref:System.Web.Security.MembershipProvider> wartość, która zawiera odpowiednie hasło mechanizmu sprawdzania poprawności.|  
|`userNamePasswordValidationMode`|Określa sposób, w których nazwy użytkownika hasło jest weryfikowane. Prawidłowe wartości to:<br /><br /> — Windows<br />-MembershipProvider<br />— Niestandardowa<br /><br /> Wartość domyślna to Windows. Ten atrybut jest typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenie do użycia w uwierzytelnianiu usługi i sprawdzanie poprawności poświadczeń klienta powiązane ustawienia.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli żaden z powiązania używane przez usługę jest skonfigurowany do uwierzytelniania opartego na nazwie/hasło użytkownika, atrybuty dla tego elementu są ignorowane. Obejmują one `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, i `userNamePasswordValidationMode`.  
  
 Jeśli żaden z powiązania używane przez usługę jest skonfigurowany do używania uwierzytelniania Windows dla nazwy użytkownika i hasła, ustawienia związane z buforowaniem tokeny logowania są ignorowane. Obejmują one `cacheLogonTokenLifetime`, `cacheLogonTokens`, i `maxCacheLogonTokens`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
