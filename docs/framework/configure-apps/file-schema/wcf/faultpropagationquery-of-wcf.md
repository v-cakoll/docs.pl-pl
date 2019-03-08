---
title: <faultPropagationQuery> w WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: e5793852d49a052d05f6cb2f4efbe166d67afc62
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675410"
---
# <a name="faultpropagationquery-of-wcf"></a>\<faultPropagationQuery > w WCF

Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.  To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia. Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania. Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.

Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).

\<system.serviceModel>\
\<Śledzenie > \
\<profiles>\
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
|`faultSourceActivityName`|Ciąg określający nazwę działanie procedury obsługi błędów, błędów. Wartość domyślna to \*, co oznacza, że dla wszystkich działań zwracane są rekordy propagacji błędów.|
|`faultHandlerActivityName`|Ciąg określający nazwę czynności, która została źródła błędu.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries-of-wcf.md)|Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.  To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.|

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [Kontrola i śledzenie przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
