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
# <a name="custom-tracking-records"></a><span data-ttu-id="9e526-102">Niestandardowe rekordy śledzenia</span><span class="sxs-lookup"><span data-stu-id="9e526-102">Custom Tracking Records</span></span>

<span data-ttu-id="9e526-103">W tym temacie pokazano, jak utworzyć niestandardowe rekordy śledzenia i wypełnić je danymi, które mają być emitowane wraz z rekordami.</span><span class="sxs-lookup"><span data-stu-id="9e526-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>

## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="9e526-104">Emitowanie niestandardowych rekordów śledzenia</span><span class="sxs-lookup"><span data-stu-id="9e526-104">Emitting Custom Tracking Records</span></span>

<span data-ttu-id="9e526-105">Niestandardowe rekordy śledzenia mogą być emitowane z działania kodu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9e526-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<span data-ttu-id="9e526-106"><xref:System.Activities.Tracking.CustomTrackingRecord> jest emitowane w działaniu kodu przez wywoływanie metody <xref:System.Activities.NativeActivityContext.Track%2A> na `ActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="9e526-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActivityContext`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e526-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e526-107">See also</span></span>

- <span data-ttu-id="9e526-108">[Monitorowanie aplikacji sieci szkieletowej systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9e526-108">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="9e526-109">[Monitorowanie aplikacji przy użyciu sieci szkieletowej aplikacji](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9e526-109">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
