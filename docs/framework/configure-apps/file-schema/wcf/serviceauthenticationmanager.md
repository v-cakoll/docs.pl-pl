---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 7708dd8a572dd24c2852410b1781fce2807efab9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263488"
---
# <a name="serviceauthenticationmanager"></a>\<serviceAuthenticationManager>
Zawiera element konfiguracji przepływu pracy, który ustanawia na poziomie usługi ważności transmisji, wiadomości i przy jego uruchomieniu.  
  
\<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceAuthenticationManager>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|serviceAuthenticationManagerType|Ciąg, który określa typ zasady uwierzytelniania dla bieżącego zachowania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
