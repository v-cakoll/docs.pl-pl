---
title: '&lt;securityTokenHandlers&gt;'
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: e63f02add81495e474b59b6c5cc090bd69add3d2
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082991"
---
# <a name="ltsecuritytokenhandlersgt"></a>&lt;securityTokenHandlers&gt;
Określa kolekcję programy obsługi tokenów zabezpieczających, które są zarejestrowane z punktem końcowym.  
  
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
|nazwa|Określa nazwę kolekcji programu obsługi tokenów. Jedynymi wartościami, które są rozpoznawane przez platformę, są "funkcję ActAs" i "OnBehalfOf". Jeśli nie określono kolekcji programu obsługi tokenów przy użyciu jednej z tych nazw, kolekcji będą używane podczas przetwarzania ActAs lub OnBehalfOf odpowiednio tokenów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|Dodaje programu obsługi tokenów zabezpieczających do kolekcji programu obsługi tokenów.|  
|[\<Wyczyść >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|Czyści wszystkie programy obsługi tokenów zabezpieczających z kolekcji programu obsługi tokenów.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|Usuwa programu obsługi tokenów zabezpieczających z kolekcji programu obsługi tokenów.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Udostępnia konfigurację dla kolekcji programy obsługi tokenów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Określa ustawienia tożsamości na poziomie usługi.|  
  
## <a name="remarks"></a>Uwagi  
 W konfiguracji usługi, można określić jeden lub więcej kolekcji o nazwie programy obsługi tokenów zabezpieczających. Można określić nazwę dla kolekcji za pomocą `name` atrybutu. Tylko nazwy, które obsługuje platformę są "funkcję ActAs" i "OnBehalfOf". Jeśli istnieją programy obsługi w tych kolekcjach, są one używane przez usługę tokenu zabezpieczającego (STS) zamiast obsługi domyślne podczas przetwarzania `ActAs` i `OnBehalfOf` tokenów.  
  
 Domyślnie kolekcja jest wypełniana przy użyciu następujące typy programów obsługi: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, i <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>. Można zmodyfikować kolekcji za pomocą `<add>`, `<remove>`, i `<clear>` elementów. Należy się upewnić, że tylko jednego obsługi określonego typu istnieje w kolekcji. Na przykład w przypadku klasy wyprowadzonej obsługi z <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> albo klasy programu obsługi lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> może zostać skonfigurowana w jednej kolekcji, ale nie oba.  
  
 Użyj `<securityTokenHandlerConfiguration>` elementu, aby określić ustawienia konfiguracji dla programów obsługi w kolekcji. Określony przez ten element zastępują ustawienia określone w usłudze za pośrednictwem [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu. Niektóre procedury obsługi (w tym niektóre typy wbudowane programów obsługi) może obsługiwać dodatkowej konfiguracji za pomocą elementu podrzędnego `<add>` elementu. Ustawienia określone na program obsługi zastąpić równoważnym ustawień określonych w kolekcji lub usługi.
