---
title: '&lt;securityTokenHandlers&gt;'
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 16827aa774a8a76f16106a8650423d0d7f084982
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritytokenhandlersgt"></a>&lt;securityTokenHandlers&gt;
Określa kolekcję programów obsługi tokenu zabezpieczeń, które są zarejestrowane z punktem końcowym.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Określa nazwę kolekcji programu obsługi tokenów. Tylko wartości, które są rozpoznawane przez platformę są "ActAs" i "OnBehalfOf". Jeśli program obsługi tokena kolekcje są określone przy użyciu jednej z następujących nazw, kolekcji będzie używany podczas przetwarzania ActAs lub OnBehalfOf odpowiednio tokenów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Dodaje programu obsługi tokenów zabezpieczających do kolekcji programu obsługi tokenów.|  
|[\<Wyczyść >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|Czyści wszystkie obsługi token zabezpieczeń z kolekcji programu obsługi tokenów.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|Usuwa programu obsługi tokenów zabezpieczeń z kolekcji programu obsługi tokenów.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Udostępnia konfiguracji dla kolekcji programu obsługi tokenów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Określa ustawienia tożsamości poziomu usług.|  
  
## <a name="remarks"></a>Uwagi  
 Można określić jedną lub więcej kolekcji nazwanych programów obsługi tokenu zabezpieczeń w konfiguracji usługi. Można określić nazwę dla kolekcji przy użyciu `name` atrybutu. Tylko nazwy, które obsługuje w ramach są "ActAs" i "OnBehalfOf". Jeśli programów obsługi istnieje w tych kolekcjach, są one używane przez usługę tokenu zabezpieczającego (STS) zamiast domyślnej obsługi podczas przetwarzania `ActAs` i `OnBehalfOf` tokenów.  
  
 Domyślnie kolekcji jest wypełniana następujące typy programów obsługi: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, i <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>. Można zmodyfikować kolekcji za pomocą `<add>`, `<remove>`, i `<clear>` elementy. Należy się upewnić, że tylko jeden obsługi określonego typu istnieje w kolekcji. Na przykład, jeśli pochodzi z obsługi <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy, albo z obsługi lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> mogą być konfigurowane w jednej kolekcji, ale nie oba.  
  
 Użyj `<securityTokenHandlerConfiguration>` element, aby określić ustawienia konfiguracji dla programów obsługi w kolekcji. Za pośrednictwem tego elementu zastępują ustawienia określone na usługi za pośrednictwem [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu. Niektóre programy obsługi (w tym kilka typów wbudowanego programu obsługi) może obsługiwać dodatkowej konfiguracji za pomocą elementu podrzędnego `<add>` elementu. Ustawienia określone na program obsługi zastąpić równoważnym ustawień określonych w kolekcji lub usługi.
