---
title: '&lt;serviceTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c25ea1fc32c93e7eb57ef8ed06d6f786ae0a670e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicetokenresolvergt"></a>&lt;serviceTokenResolver&gt;
Rejestruje mechanizm rozpoznawania tokenu usługi, używany przez programy obsługi zdarzeń w kolekcji programu obsługi tokenów. Program rozpoznawania nazw tokenów usługi jest używany do rozpoznawania tokenu szyfrowania na przychodzące tokeny i komunikatów.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration >  
\<serviceTokenResolver >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
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
|— typ|Określa typ usługi program rozpoznawania nazw tokenów. Albo <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typu lub typu pochodzącego od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy. Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołania do typu niestandardowego]. Wymagana.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Zapewnia token obsługi konfiguracji dla kolekcji zabezpieczeń.|  
  
## <a name="remarks"></a>Uwagi  
 Program rozpoznawania nazw tokenów usług można rozpoznać tokenu szyfrowania na przychodzące tokeny i komunikatów. Służy do pobierania klucza, które mają być używane do odszyfrowywania tokenów przychodzących. Należy określić `type` atrybutu. Określony typ może być <xref:System.IdentityModel.Selectors.SecurityTokenResolver> lub pochodzącego od typu niestandardowego <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy.  
  
 Niektóre obsługi tokenów umożliwiają określenie ustawień rozpoznawania tokenu usługi w konfiguracji. Ustawienia dotyczące poszczególnych programu obsługi tokenów zastąpić określonej w kolekcji programu obsługi tokenów zabezpieczeń.  
  
> [!NOTE]
>  Określanie `<serviceTokenResolver>` element jako element podrzędny elementu [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element jest przestarzała, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami. Ustawienia na `<securityTokenHandlerConfiguration>` element przesłaniają akcje na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Przykład  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
