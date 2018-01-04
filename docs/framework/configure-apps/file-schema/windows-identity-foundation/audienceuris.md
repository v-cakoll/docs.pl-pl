---
title: '&lt;audienceUris&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 69c96698b309a789b4527c76e1fe8b8b99811a19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltaudienceurisgt"></a>&lt;audienceUris&gt;
Określa zestaw identyfikatorów URI, które są dopuszczalne identyfikatory uzależnionej (RP). Tokeny nie będą akceptowane, chyba że ograniczone do jednej z dozwolonych odbiorców identyfikatorów URI.  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<securityTokenHandlerConfiguration >  
\<audienceUris >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|tryb|<xref:System.IdentityModel.Selectors.AudienceUriMode> Wartość, która określa, czy ograniczenie odbiorców powinien być zastosowany przychodzącym tokenie. Możliwe wartości to "Always", "Nigdy" i "BearerKeyOnly". Wartość domyślna to "Always". Opcjonalny.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`<add value=xs:string>`|Dodaje określony przez identyfikator URI `value` atrybutu do kolekcji audienceUris. `value` Atrybut jest wymagany. Identyfikator URI jest rozróżniana wielkość liter.|  
|`<clear>`|Czyści kolekcję audienceUris. Wszystkie identyfikatory zostaną usunięte z kolekcji.|  
|`<remove value=xs:string>`|Usuwa określony przez identyfikator URI `value` atrybutu z kolekcji audienceUris. `value` Atrybut jest wymagany. Identyfikator URI jest rozróżniana wielkość liter.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Zapewnia token obsługi konfiguracji dla kolekcji zabezpieczeń.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie kolekcji jest pusty; Użyj `<add>`, `<clear>`, i `<remove>` elementy, aby modyfikować kolekcji. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>i <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> obiekty używają wartości do kolekcji identyfikatora URI odbiorców do skonfigurowania wszystkich dozwolone odbiorców ograniczenia identyfikatora URI w <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiektów.  
  
 `<audienceUris>` Reprezentowany przez element <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> klasy. URI poszczególnych dodać do kolekcji jest reprezentowane przez <xref:System.IdentityModel.Configuration.AudienceUriElement> klasy.  
  
> [!NOTE]
>  Korzystanie z `<audienceUris>` element jako element podrzędny elementu [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element jest przestarzała, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami. Ustawienia na `<securityTokenHandlerConfiguration>` element przesłaniają akcje na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Przykład  
 Następujący kod XML przedstawiono sposób konfigurowania odbiorców dopuszczalne identyfikatorów URI dla aplikacji. Ten przykład konfiguruje pojedynczy identyfikator URI. Tokeny tego identyfikatora URI w zakresie będą akceptowane, wszystkie pozostałe zostaną odrzucone.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
