---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 556c444d5e48e27036c4b49338f6e70de7ef5c5d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267278"
---
# <a name="audienceuris"></a>\<audienceUris>
Określa zbiór identyfikatorów URI, które są dopuszczalne identyfikatorów jednostki uzależnionej strony (RP). Tokeny nie będą akceptowane, chyba że są one w zakresie dla jednej z dozwolonych odbiorców identyfikatorów URI.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<audienceUris>  
  
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
|tryb|<xref:System.IdentityModel.Selectors.AudienceUriMode> Wartość, która określa, czy ograniczenie odbiorców powinny być stosowane do przychodzący token. Możliwe wartości to "Zawsze", "Nie" i "BearerKeyOnly". Wartość domyślna to "Always". Opcjonalna.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`<add value=xs:string>`|Dodaje określony przez identyfikator URI `value` atrybutu do kolekcji audienceUris. `value` Atrybut jest wymagany. Identyfikator URI jest rozróżniana wielkość liter.|  
|`<clear>`|Czyści kolekcję audienceUris. Wszystkie identyfikatory są usuwane z kolekcji.|  
|`<remove value=xs:string>`|Usuwa określony przez identyfikator URI `value` atrybutu z kolekcji audienceUris. `value` Atrybut jest wymagany. Identyfikator URI jest rozróżniana wielkość liter.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie kolekcja jest pusta, Użyj `<add>`, `<clear>`, i `<remove>` elementy, aby zmodyfikować kolekcji. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> i <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> obiekty wartości w kolekcji identyfikatora URI grupy odbiorców do skonfigurowania wszystkich dozwolone odbiorców ograniczeń identyfikatora URI w użycie <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiektów.  
  
 `<audienceUris>` Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> klasy. Identyfikator URI poszczególnych dodawane do kolekcji jest reprezentowany przez <xref:System.IdentityModel.Configuration.AudienceUriElement> klasy.  
  
> [!NOTE]
>  Korzystanie z `<audienceUris>` element jako element podrzędny [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu jest przestarzałe, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami. Ustawienia na `<securityTokenHandlerConfiguration>` elemencie przesłaniają akcje na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Przykład  
 Następujący kod XML przedstawia sposób konfigurowania odbiorców dopuszczalne identyfikatorów URI dla aplikacji. Ten przykład umożliwia skonfigurowanie pojedynczego identyfikatora URI. Akceptowane są tokeny zakresu dla tego identyfikatora URI, wszystkie pozostałe zostaną odrzucone.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
