---
title: Niestandardowe rekordy śledzenia
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 986f0350c24414d0ff960474445adf6ac3f39734
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802625"
---
# <a name="custom-tracking-records"></a>Niestandardowe rekordy śledzenia

W tym temacie pokazano, jak utworzyć niestandardowe rekordy śledzenia i wypełnić je danymi, które mają być emitowane wraz z rekordami.

## <a name="emitting-custom-tracking-records"></a>Emitowanie niestandardowych rekordów śledzenia

Niestandardowe rekordy śledzenia mogą być emitowane z działania kodu, jak pokazano w poniższym przykładzie.

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<xref:System.Activities.Tracking.CustomTrackingRecord> jest emitowane w działaniu kodu przez wywoływanie metody <xref:System.Activities.NativeActivityContext.Track%2A> na `ActivityContext`.

## <a name="see-also"></a>Zobacz także

- [Monitorowanie aplikacji sieci szkieletowej systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorowanie aplikacji przy użyciu sieci szkieletowej aplikacji](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
