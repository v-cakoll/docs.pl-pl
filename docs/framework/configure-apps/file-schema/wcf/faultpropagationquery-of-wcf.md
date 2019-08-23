---
title: <faultPropagationQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: 6ba6478ca500c0a8ef150966a97898f8743ffdf8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925632"
---
# <a name="faultpropagationquery-of-wcf"></a>\<faultPropagationQuery > WCF

Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.  To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd. Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania. Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.

Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).

\<system.serviceModel>\
\<Śledzenie > \
\<Profile > \
\<trackingProfile>\
\<przepływ pracy > \
\<faultPropagationQueries>\
\<faultPropagationQuery>

## <a name="syntax"></a>Składnia

```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String" />
        </faultPropagationQueries>
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
|`faultSourceActivityName`|Ciąg określający nazwę działania procedury obsługi błędu, które propaguje błąd. Wartość domyślna to \*, co oznacza, że rekordy propagacji błędów są zwracane dla wszystkich działań.|
|`faultHandlerActivityName`|Ciąg określający nazwę czynności, która została źródła błędu.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries-of-wcf.md)|Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.  To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.|

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [Kontrola i śledzenie przepływu pracy](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Profile śledzenia](../../../windows-workflow-foundation/tracking-profiles.md)
