---
title: '&lt;UserNameAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: d81bf3441f4999683b9dc9ab956fff517c20e80e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754866"
---
# <a name="ltusernameauthenticationgt"></a>&lt;UserNameAuthentication&gt;
Określa poświadczenia usługi na podstawie nazwy użytkownika i hasła.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<userNameAuthentication >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<userNameAuthentication  
   cacheLogonTokenLifetime="TimeSpan"  
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
|`cacheLogonTokenLifetime`|A <xref:System.TimeSpan> , który określa maksymalną długość czasu tokenu są buforowane. Wartość domyślna to 00:15:00.|  
|`cacheLogonTokens`|Wartość logiczna określająca, czy tokeny logowania są buforowane. Wartość domyślna to `false`.|  
|`customUserNamePasswordValidatorType`|Ciąg określający typ Walidatora niestandardowej nazwy użytkownika hasło do użycia. Wartość domyślna to ciąg pusty.|  
|`includeWindowsGroups`|Wartość logiczna określająca, czy grupy systemu Windows znajdują się w kontekście zabezpieczeń. Wartość domyślna to `true`.<br /><br /> Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ jej wynikiem rozszerzenia grupy pełnej. Ta właściwość jest ustawiana `false` Jeśli nie musisz ustanowić listę grup należy użytkownik.|  
|`maxCacheLogonTokens`|Liczba całkowita określająca maksymalną liczbę tokenów logowania do pamięci podręcznej. Ta wartość powinna być większa niż zero. Wartość domyślna to 128.|  
|`membershipProviderName`|Gdy `clientCredentialType` ustawiono atrybut powiązania `username`, nazwa użytkownika jest mapowana na konta systemu Windows. Użytkownik może zmienić to zachowanie przy użyciu tego atrybutu, który jest ciąg znaków zawierający nazwę <xref:System.Web.Security.MembershipProvider> wartość, która zapewnia mechanizm weryfikacji odpowiednie hasło.|  
|`userNamePasswordValidationMode`|Określa sposób, w których nazwy użytkownika hasło jest weryfikowane. Prawidłowe wartości to:<br /><br /> — Windows<br />-MembershipProvider.<br />-Niestandardowe<br /><br /> Wartość domyślna to Windows. Ten atrybut jest typu <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenia, które ma być używany podczas uwierzytelniania usługi, i sprawdzanie poprawności poświadczeń klienta powiązane ustawienia.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli żaden z powiązania używane przez usługę jest skonfigurowany do uwierzytelniania opartego na nazwie/hasło użytkownika, są ignorowane atrybutów dla tego elementu. Obejmują one `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, i `userNamePasswordValidationMode`.  
  
 Jeśli żaden z powiązania używane przez usługę jest skonfigurowany do uwierzytelniania systemu Windows dla nazwy użytkownika i hasła, ustawienia związane z buforowaniem tokenów logowania są ignorowane. Obejmują one `cacheLogonTokenLifetime`, `cacheLogonTokens`, i `maxCacheLogonTokens`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
