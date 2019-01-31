---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 1143717882652fc8a03947327b5f1ea89dde7373
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267433"
---
# <a name="servicetokenresolver"></a>\<serviceTokenResolver>
Rejestruje usługę program rozpoznawania tokenów, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów. Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania na przychodzące tokeny i komunikatów.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration>  
\<serviceTokenResolver>  
  
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
|— typ|Określa typ program rozpoznawania tokenów usługi. Albo <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typu lub typ pochodzący z <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy. Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do niestandardowego typu]. Wymagana.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.|  
  
## <a name="remarks"></a>Uwagi  
 Program rozpoznawania tokenów usługi można rozpoznać tokenu szyfrowania na przychodzące tokeny i komunikatów. Służy do pobierania klucza, które mają być używane do odszyfrowywania tokenów przychodzących. Należy określić `type` atrybutu. Określony typ może być <xref:System.IdentityModel.Selectors.SecurityTokenResolver> lub typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy.  
  
 Niektóre programy obsługi tokenów umożliwiają określanie ustawień program rozpoznawania tokenów usługi w konfiguracji. Ustawienia dotyczące programu obsługi tokenów poszczególnych zastąpienia określonej w kolekcji programu obsługi tokenów zabezpieczeń.  
  
> [!NOTE]
>  Określanie `<serviceTokenResolver>` element jako element podrzędny [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu jest przestarzałe, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami. Ustawienia na `<securityTokenHandlerConfiguration>` elemencie przesłaniają akcje na `<identityConfiguration>` elementu.  
  
## <a name="example"></a>Przykład  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
