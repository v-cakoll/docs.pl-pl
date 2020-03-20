---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152583"
---
# <a name="servicetokenresolver"></a>\<> serviceTokenResolver
Rejestruje program rozpoznawania tokenów usługi, który jest używany przez programy obsługi w kolekcji obsługi tokenu. Program rozpoznawania nazw tokenów usługi służy do rozpoznawania tokenu szyfrowania na przychodzących tokenach i wiadomościach.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>securityTokenHandlers**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji securityTokenHandler**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>serviceTokenResolver**  
  
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
|type|Określa typ programu rozpoznawania tokenów usługi. Typ <xref:System.IdentityModel.Selectors.SecurityTokenResolver> lub typ, który pochodzi od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> klasy. Aby uzyskać więcej informacji `type` na temat określania atrybutu, zobacz [Odwołania do typów niestandardowych]. Wymagany.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>konfiguracji securityTokenHandler](securitytokenhandlerconfiguration.md)|Zapewnia konfigurację dla kolekcji obsługi tokenów zabezpieczających.|  
  
## <a name="remarks"></a>Uwagi  
 Program rozpoznawania nazw tokenów usługi może służyć do rozpoznawania tokenu szyfrowania na przychodzących tokenów i wiadomości. Służy do pobierania klucza, który powinien służyć do odszyfrowywania tokenów przychodzących. Należy określić `type` atrybut. Określony typ może być <xref:System.IdentityModel.Selectors.SecurityTokenResolver> albo typu niestandardowego, <xref:System.IdentityModel.Selectors.SecurityTokenResolver> który pochodzi od klasy.  
  
 Niektóre programy obsługi tokenu umożliwiają określenie ustawień rozpoznawania nazw tokenów usługi w konfiguracji. Ustawienia poszczególnych programów obsługi tokenów zastępują te określone w kolekcji obsługi tokenów zabezpieczających.  
  
> [!NOTE]
> Określanie `<serviceTokenResolver>` elementu jako elementu podrzędnego [ \<identityConfiguration>](identityconfiguration.md) element został przestarzały, ale nadal jest obsługiwany dla zgodności z powrotem. Ustawienia elementu `<securityTokenHandlerConfiguration>` zastąpić te na `<identityConfiguration>` elemencie.  
  
## <a name="example"></a>Przykład  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
