---
title: <windowsAuthentication> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ded04f6e87fce2e12dac8f681ba2d4178f8fd204
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399112"
---
# <a name="windowsauthentication-of-servicecredentials"></a>\<windowsAuthentication> dla \<serviceCredentials>
Określa ustawienia poświadczenia usługi systemu Windows.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`includeWindowsGroups`|Opcjonalny atrybut logiczny, który określa, czy system zawiera grupy systemu Windows w kontekście zabezpieczeń. Wartość domyślna to `true`.<br /><br /> Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ skutkuje rozwinięciem całej grupy. Ustaw ten atrybut na `false` , jeśli nie ma potrzeby ustanawiania listy grup, do których należy użytkownik.|  
|`allowAnonymousLogons`|Opcjonalny atrybut logiczny, który określa, czy są dozwolone anonimowe, nieuwierzytelnione wywoływania. Wartość domyślna to `false`.<br /><br /> Gdy `clientCredentialType` atrybut powiązania jest ustawiony na `Windows` , system nie zezwala na anonimowe wywołania. Oznacza to, że w celu uzyskania dostępu do systemu są dozwolone tylko uwierzytelnione wywołania domeny lub grupy roboczej. To zachowanie można zastąpić za pomocą tego atrybutu.<br /><br /> Użyj tego ustawienia z największą ostrożnością.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj tego elementu, aby określić, czy zezwolić na dostęp anonimowym użytkownikom systemu Windows przez ustawienie `allowAnonymousLogons` atrybutu. Można również określić, czy mają zostać dołączone informacje o grupie, do których użytkownicy należą do AuthorizationContext przez ustawienie `includeWindowsGroups` atrybutu. Jeśli jest ustawiona na `true` (ustawienie domyślne), usługa może określić grupy systemu Windows, do których należy klient.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
