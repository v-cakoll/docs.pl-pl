---
title: <customTrackingQuery> w WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 0a5e7c034ce1ef12a8d7d5b1753e2e441e48e293
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673176"
---
# <a name="customtrackingquery-of-wcf"></a>\<customTrackingQuery > w WCF

Reprezentuje zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu. Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.

Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<Śledzenie >  
\<profiles>  
\<trackingProfile>  
\<przepływ pracy >  
\<customTrackingQueries>  
\<customTrackingQuery>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`activityName`|Ciąg określający nazwę działania, który wygenerował rekord śledzenia.|  
|`name`|Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.|  
  
### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|  
|-------------|-----------------|  
|[\<customTrackingQueries>](customtrackingqueries-of-wcf.md)|Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.|
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [Kontrola i śledzenie przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
