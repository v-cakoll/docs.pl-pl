---
title: '&lt;limity czasu&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: e39deeb251865b87eb7734e4447088ca2f221d1d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148334"
---
# <a name="lttimeoutsgt"></a>&lt;limity czasu&gt;
Reprezentuje element konfiguracji, który określa przedział czasu dozwolony usługi hosta na otwarcie lub zamknięcie.  
  
 \<system.ServiceModel>  
\<Klient >  
\<punkt końcowy >  
\<host >  
\<limity czasu >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`closeTimeout`|A <xref:System.TimeSpan> wartość, która określa przedział czasu dozwolony na zamknięcie usługi hosta.|  
|`openTimeout`|A <xref:System.TimeSpan> wartość, która określa okres czasu dozwolony dla otwarcie usługi hosta.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<host >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Element konfiguracji, który określa ustawienia dla usługi hosta.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [Hosting](../../../../../docs/framework/wcf/feature-details/hosting.md)
