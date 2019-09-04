---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 30a53c11b551623311f7ca3f957143fc702568a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251849"
---
# <a name="servicetokenresolver"></a>\<serviceTokenResolver>
Rejestruje program rozpoznawania tokenów usługi używany przez programy obsługi w kolekcji obsługi tokenów. Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania przychodzących tokenów i komunikatów.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceTokenResolver >**  
  
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
 