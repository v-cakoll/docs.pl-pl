---
title: Niestandardowe rekordy śledzenia
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: d4733b4ffc0d866cf90fd5a5e7d649de261c45fb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499124"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="663d8-102">Niestandardowe rekordy śledzenia</span><span class="sxs-lookup"><span data-stu-id="663d8-102">Custom Tracking Records</span></span>

<span data-ttu-id="663d8-103">W tym temacie pokazano, jak utworzyć niestandardowe rekordy śledzenia i wypełnić je danymi jest emitowany wraz z rekordów.</span><span class="sxs-lookup"><span data-stu-id="663d8-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>

## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="663d8-104">Emitowanie niestandardowe rekordy śledzenia</span><span class="sxs-lookup"><span data-stu-id="663d8-104">Emitting Custom Tracking Records</span></span>

<span data-ttu-id="663d8-105">Niestandardowe rekordy śledzenia może być emitowana działania kodu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="663d8-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<span data-ttu-id="663d8-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> emitowane w działaniu kodu, wywołując <xref:System.Activities.NativeActivityContext.Track%2A> metody `ActivityContext`.</span><span class="sxs-lookup"><span data-stu-id="663d8-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActivityContext`.</span></span>

## <a name="see-also"></a><span data-ttu-id="663d8-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="663d8-107">See also</span></span>

- [<span data-ttu-id="663d8-108">Windows Server AppFabric monitorowania</span><span class="sxs-lookup"><span data-stu-id="663d8-108">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="663d8-109">Monitorowanie aplikacji przy użyciu rozwiązania AppFabric</span><span class="sxs-lookup"><span data-stu-id="663d8-109">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
