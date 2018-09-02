---
title: '&lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 596cab4494ef3ba200fd0a046d7935f648fb7c4f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422191"
---
# <a name="ltremovegt"></a>&lt;remove&gt;
Usuwa programu obsługi tokenów zabezpieczeń określone z kolekcji programu obsługi tokenów.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<Usuń >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|— typ|Nazwa typu CLR programu obsługi tokenów do usunięcia. Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do typu niestandardowego](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24). Wymagane.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Określa kolekcję programy obsługi tokenów zabezpieczających, które są zarejestrowane z punktem końcowym.|  
  
## <a name="example"></a>Przykład  
 Następujący kody XML pokazuje użycie `<add>` i `<remove>` elementów, aby zastąpić domyślne sesji programu obsługi tokenów niestandardową sesję programu obsługi tokenów. Kod XML jest pobierana z `ClaimsAwareWebFarm` próbki.  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
