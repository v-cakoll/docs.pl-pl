---
title: '&lt;Typ oświadczenia&gt;'
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 94f8586a9ca63b8c1f1128cdda4a74ccfe0f5416
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimtypegt"></a>&lt;Typ oświadczenia&gt;
Określa pojedynczy opcjonalne lub wymagane oświadczenia przychodzące tokeny zabezpieczające.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<claimTypeRequired >  
\<Element claimType >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|— typ|Typ oświadczenia. Zazwyczaj identyfikator URI. Wymagana.|  
|optional|Wartość logiczna określająca, czy typ oświadczenia jest opcjonalna. Opcjonalna.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<claimTypeRequired >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|Określa zestaw żądanych oświadczeń przychodzących tokenów zabezpieczających.|
