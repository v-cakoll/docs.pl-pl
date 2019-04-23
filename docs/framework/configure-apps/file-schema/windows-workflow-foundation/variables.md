---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 61a786efc67f4e9afa585864e1f62b966b5cdff8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105381"
---
# <a name="variables"></a>\<Zmienne >
Reprezentuje kolekcję zmiennych skojarzoną z tym zapytaniem działania.  
  
 Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
\<system.serviceModel>  
\<Śledzenie >  
\<trackingProfile>  
\<przepływ pracy >  
\<activityStateQueries>  
\<activityStateQuery>  
\<Zmienne >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zmienna >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|Zmienna skojarzonych z kwerendą stanu działania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|Reprezentuje element konfiguracji, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne. Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.|  
  
## <a name="remarks"></a>Uwagi  
 Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy. Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania. Możesz użyć [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolnej zmiennej lub argumentu wszelkie działania w przepływie pracy. W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane. Zmienne i argumenty wyodrębniania tylko z ActivityStateRecord i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [Kontrola i śledzenie przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
