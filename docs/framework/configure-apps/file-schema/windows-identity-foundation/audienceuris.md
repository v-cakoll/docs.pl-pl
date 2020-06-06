---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: bd04e4ebdf5c58adaeea0ff0ca5993d7d9ce38f1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252170"
---
# \<audienceUris>
Określa zestaw identyfikatorów URI, które są akceptowalnymi identyfikatorami jednostki uzależnionej (RP). Tokeny nie zostaną zaakceptowane, chyba że zostaną objęte zakresem jednego z dozwolonych identyfikatorów URI odbiorców.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
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
|tryb|Wartość określająca <xref:System.IdentityModel.Selectors.AudienceUriMode> , czy ograniczenie odbiorców ma być stosowane do tokenu przychodzącego. Możliwe wartości to "always", "Never" i "BearerKeyOnly". Wartość domyślna to "zawsze". Opcjonalny.|  
  
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
 Domyślnie kolekcja jest pusta; Użyj `<add>` `<clear>` elementów, i, `<remove>` Aby zmodyfikować kolekcję. <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler><xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>obiekty i używają wartości w kolekcji identyfikatorów URI odbiorców w celu skonfigurowania dozwolonych ograniczeń identyfikatorów URI odbiorców w <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiektach.  
  
 `<audienceUris>`Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> klasę. Pojedynczy identyfikator URI dodany do kolekcji jest reprezentowany przez <xref:System.IdentityModel.Configuration.AudienceUriElement> klasę.  
  
> [!NOTE]
> Użycie `<audienceUris>` elementu jako elementu podrzędnego [\<identityConfiguration>](identityconfiguration.md) elementu jest przestarzałe, ale nadal jest ono obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami. Ustawienia w `<securityTokenHandlerConfiguration>` elemencie Przesłoń te elementy w `<identityConfiguration>` elemencie.  
  
## <a name="example"></a>Przykład  
 Poniższy kod XML przedstawia sposób konfigurowania akceptowalnych identyfikatorów URI odbiorców dla aplikacji. Ten przykład umożliwia skonfigurowanie pojedynczego identyfikatora URI. Tokeny należące do zakresu dla tego identyfikatora URI zostaną zaakceptowane. wszystkie pozostałe zostaną odrzucone.  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
