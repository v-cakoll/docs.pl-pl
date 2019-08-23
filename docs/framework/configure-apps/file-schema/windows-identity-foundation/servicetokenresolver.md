---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 69d34cb54c2236f178ac4291ed24a3f5b45db48e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923109"
---
# <a name="servicetokenresolver"></a>\<serviceTokenResolver>
Rejestruje program rozpoznawania tokenów usługi używany przez programy obsługi w kolekcji obsługi tokenów. Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania przychodzących tokenów i komunikatów.  
  
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
|— typ|Określa typ programu rozpoznawania tokenów usług. Typ lub typ, który pochodzi <xref:System.IdentityModel.Selectors.SecurityTokenResolver> od klasy. <xref:System.IdentityModel.Selectors.SecurityTokenResolver> Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych]. Wymagana.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.|  
  
## <a name="remarks"></a>Uwagi  
 Program rozpoznawania tokenów usług może służyć do rozwiązywania tokenu szyfrowania przychodzących tokenów i komunikatów. Służy do pobierania klucza, który ma być używany do odszyfrowywania tokenów przychodzących. Należy określić `type` atrybut. Określony typ może być albo <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typem niestandardowym, który pochodzi <xref:System.IdentityModel.Selectors.SecurityTokenResolver> od klasy.  
  
 Niektóre programy obsługi tokenów umożliwiają określanie ustawień programu rozpoznawania tokenów usług w konfiguracji. Ustawienia poszczególnych programów obsługi tokenów przesłaniają te określone w kolekcji obsługi tokenów zabezpieczających.  
  
> [!NOTE]
> Określanie elementu jako elementu [ \<](identityconfiguration.md) podrzędnego elementu IdentityConfiguration > jest przestarzałe, ale nadal jest on obsługiwany w celu zapewnienia zgodności z poprzednimi wersjami. `<serviceTokenResolver>` Ustawienia w `<securityTokenHandlerConfiguration>` elemencie Przesłoń te elementy `<identityConfiguration>` w elemencie.  
  
## <a name="example"></a>Przykład  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
