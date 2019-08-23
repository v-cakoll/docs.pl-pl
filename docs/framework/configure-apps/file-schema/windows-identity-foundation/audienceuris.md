---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 003221ed4dc7f4ccf72d2e0d3a91265e13172813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941961"
---
# <a name="audienceuris"></a>\<audienceUris>
Określa zestaw identyfikatorów URI, które są akceptowalnymi identyfikatorami jednostki uzależnionej (RP). Tokeny nie zostaną zaakceptowane, chyba że zostaną objęte zakresem jednego z dozwolonych identyfikatorów URI odbiorców.  
  
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
|tryb|<xref:System.IdentityModel.Selectors.AudienceUriMode> Wartość określająca, czy ograniczenie odbiorców ma być stosowane do tokenu przychodzącego. Możliwe wartości to "always", "Never" i "BearerKeyOnly". Wartość domyślna to "zawsze". Opcjonalny.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`<add value=xs:string>`|Dodaje identyfikator URI określony przez `value` atrybut do kolekcji audienceUris. `value` Atrybut jest wymagany. W identyfikatorze URI jest rozróżniana wielkość liter.|  
|`<clear>`|Czyści kolekcję audienceUris. Wszystkie identyfikatory są usuwane z kolekcji.|  
|`<remove value=xs:string>`|Usuwa identyfikator URI określony przez `value` atrybut z kolekcji audienceUris. `value` Atrybut jest wymagany. W identyfikatorze URI jest rozróżniana wielkość liter.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie kolekcja jest pusta; Użyj `<add>`elementów `<clear>`, i`<remove>` , aby zmodyfikować kolekcję. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>obiekty <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> i używają wartości w kolekcji identyfikatorów URI odbiorców w celu skonfigurowania dozwolonych ograniczeń identyfikatorów URI <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> odbiorców w obiektach.  
  
 Element jest reprezentowany <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> przez klasę. `<audienceUris>` Pojedynczy identyfikator URI dodany do kolekcji jest reprezentowany przez <xref:System.IdentityModel.Configuration.AudienceUriElement> klasę.  
  
> [!NOTE]
> Użycie `<audienceUris>` elementu jako elementu [ \<](identityconfiguration.md) podrzędnego elementu IdentityConfiguration > jest przestarzałe, ale nadal jest obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami. Ustawienia w `<securityTokenHandlerConfiguration>` elemencie Przesłoń te elementy `<identityConfiguration>` w elemencie.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML przedstawia sposób konfigurowania akceptowalnych identyfikatorów URI odbiorców dla aplikacji. Ten przykład umożliwia skonfigurowanie pojedynczego identyfikatora URI. Tokeny należące do zakresu dla tego identyfikatora URI zostaną zaakceptowane. wszystkie pozostałe zostaną odrzucone.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
