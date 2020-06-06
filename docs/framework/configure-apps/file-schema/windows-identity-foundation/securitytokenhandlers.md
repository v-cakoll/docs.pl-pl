---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 017309436660991c69da569e9cc4219e842ecaa3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251874"
---
# \<securityTokenHandlers>
Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
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
|name|Określa nazwę kolekcji obsługi tokenów. Jedyne wartości rozpoznawane przez platformę to "ActAs" i "OnBehalfOf". Jeśli kolekcje obsługi tokenów są określone przy użyciu jednej z tych nazw, kolekcja zostanie użyta podczas przetwarzania tokenów ActAs lub OnBehalfOf.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](add.md)|Dodaje procedurę obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.|  
|[\<clear>](clear.md)|Czyści wszystkie programy obsługi tokenów zabezpieczających z kolekcji obsługi tokenów.|  
|[\<remove>](remove.md)|Usuwa procedurę obsługi tokenu zabezpieczającego z kolekcji obsługi tokenów.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Zapewnia konfigurację kolekcji programów obsługi tokenów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Określa ustawienia tożsamości na poziomie usług.|  
  
## <a name="remarks"></a>Uwagi  
 W konfiguracji usługi można określić co najmniej jedną nazwę kolekcji programów obsługi tokenów zabezpieczających. Możesz określić nazwę kolekcji przy użyciu `name` atrybutu. Jedyne nazwy obsługiwane przez platformę to "ActAs" i "OnBehalfOf". Jeśli w tych kolekcjach istnieją programy obsługi, są one używane przez usługę tokenu zabezpieczającego (STS) zamiast domyślnych programów obsługi podczas przetwarzania `ActAs` i `OnBehalfOf` tokenów.  
  
 Domyślnie kolekcja jest wypełniana następującymi typami obsługi:,,,, <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> , i <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> . Kolekcję można modyfikować za pomocą `<add>` `<remove>` elementów, i `<clear>` . Musisz się upewnić, że w kolekcji istnieje tylko jedna procedura obsługi określonego typu. Na przykład, jeśli pochodna jest procedura obsługi z <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy, program obsługi lub <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> może być skonfigurowany w pojedynczej kolekcji, ale nie w obu tych przypadkach.  
  
 Użyj `<securityTokenHandlerConfiguration>` elementu, aby określić ustawienia konfiguracji dla programów obsługi w kolekcji. Ustawienia określone za pomocą tego elementu zastępują te określone w usłudze za pomocą [\<identityConfiguration>](identityconfiguration.md) elementu. Niektóre programy obsługi (w tym kilka wbudowanych typów obsługi) mogą obsługiwać dodatkową konfigurację za pomocą elementu podrzędnego `<add>` elementu. Ustawienia określone w ustawieniach przesłonięcia programu obsługi określone w kolekcji lub usłudze.
