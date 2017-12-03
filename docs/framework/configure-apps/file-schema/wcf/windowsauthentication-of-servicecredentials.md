---
title: '&lt;windowsAuthentication&gt; w &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8af7d89fdf09316594bc8ef3433e2b47e8fb0a7e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltwindowsauthenticationgt-of-ltservicecredentialsgt"></a>&lt;windowsAuthentication&gt; w &lt;serviceCredentials&gt;
Określa ustawienia poświadczenia usługi systemu Windows.  
  
 \<System. ServiceModel >  
\<zachowania >  
\<serviceBehaviors >  
\<zachowanie >  
\<serviceCredentials >  
\<windowsAuthentication >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<windowsAuthentication  
      allowAnonymousLogons="Boolean"  
      includeWindowsGroups="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`includeWindowsGroups`|Opcjonalny logiczny atrybut, który określa, czy system zawiera grupy systemu Windows w kontekście zabezpieczeń. Wartość domyślna to `true`.<br /><br /> Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ jej wynikiem rozszerzenia grupy pełnej. Ten atrybut na `false` Jeśli nie musisz ustanowić listę grup należy użytkownik.|  
|`allowAnonymousLogons`|Opcjonalny logiczny atrybut, który określa, czy są dozwolone anonimowe, nieuwierzytelnione wywoływania. Wartość domyślna to `false`.<br /><br /> Gdy `clientCredentialType` ustawiono atrybut powiązania `Windows`, systemu nie zezwala na anonimowe obiekty wywołujące. Oznacza to, że tylko domeny lub grupy roboczej uwierzytelniony elementy wywołujące mogą uzyskać dostępu do systemu. Aby zmienić to zachowanie, należy za pomocą tego atrybutu.<br /><br /> Użyj tego ustawienia z najwyższą ostrożność.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenia do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj tego elementu, aby określić, czy zezwolić na dostęp do anonimowych użytkowników systemu Windows przez ustawienie `allowAnonymousLogons` atrybutu. Można również określić, czy do uwzględnienia informacji o grupie, do której należą użytkowników w elementu AuthorizationContext przez ustawienie `includeWindowsGroups` atrybutu. Jeśli wartość jest ustawiona na `true` (ustawienie domyślne), ta usługa może określić grupy systemu Windows, do której należy dany klient.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.WindowsServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>
