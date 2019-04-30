---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 266b33e9b0386d0346a86ba8bd82cc65def4f0c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673059"
---
# <a name="endtoendtracing"></a>\<endToEndTracing >
Element konfiguracji, który umożliwia włączanie i wyłączanie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.  
  
 \<system.ServiceModel>  
\<diagnostyczne >  
\<endToEndTracing >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`activityTracing`|Wartość logiczna określająca, czy czynność śledzenia jest włączona.|  
|`messageFlowTracing`|Wartość logiczna określająca, czy jest włączone śledzenie przepływu wiadomości.|  
|`propagateActivity`|Wartość logiczna określająca, czy propagowany atrybut jest ustawiony na wartość true.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Diagnostyka >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Definiuje ustawienia WCF dla środowiska uruchomieniowego kontroli i kontroli dla administratora.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [Kompleksowe śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
