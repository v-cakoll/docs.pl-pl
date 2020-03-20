---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152791"
---
# <a name="certificatevalidator"></a>\<certyfikatValidator>
Określa typ niestandardowy sprawdzania poprawności certyfikatu. Ten typ jest używany `certificateValidationMode` tylko wtedy, gdy atrybut [ \<certificateValidation>](certificatevalidation.md) element jest ustawiony na "Niestandardowe".  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>certyfikatuWeracja**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certyfikatValidator>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|type|Określa typ niestandardowy, który <xref:System.IdentityModel.Selectors.X509CertificateValidator> pochodzi z klasy. Ustaw `certificateValidationMode` atrybut [ \<certificateValidation>](certificatevalidation.md) element na "Niestandardowe", aby użyć tego typu. Aby uzyskać więcej informacji `type` na temat określania atrybutu, zobacz [Odwołania do typów niestandardowych](../windows-workflow-foundation/index.md). Element opcjonalny.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>certyfikatuWeracja](certificatevalidation.md)|Steruje ustawieniami używanymi przez programy obsługi tokenów do sprawdzania poprawności certyfikatów.|  
  
## <a name="example"></a>Przykład  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
