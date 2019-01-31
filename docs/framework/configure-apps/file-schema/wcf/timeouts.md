---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 8a8a352380fe6eedb41ead089405e7b79fad29fe
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272786"
---
# <a name="timeouts"></a>\<timeOuts>
Reprezentuje element konfiguracji, który określa przedział czasu dozwolony usługi hosta na otwarcie lub zamknięcie.  
  
 \<system.ServiceModel>  
\<client>  
\<punkt końcowy >  
\<host>  
\<timeOuts>  
  
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
|[\<host>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Element konfiguracji, który określa ustawienia dla usługi hosta.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [Hosting](../../../../../docs/framework/wcf/feature-details/hosting.md)
