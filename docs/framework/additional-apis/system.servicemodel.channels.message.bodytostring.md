---
title: Message. BodyToString — Metoda (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 9f1f852c0bd82299fd40afe66a5f90cd7c0335cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215504"
---
# <a name="messagebodytostring-method"></a><span data-ttu-id="c733e-102">Message. BodyToString — Metoda</span><span class="sxs-lookup"><span data-stu-id="c733e-102">Message.BodyToString Method</span></span>

<span data-ttu-id="c733e-103">Konwertuje treść komunikatu na ciąg, wywołując metodę <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c733e-103">Converts the message body into a string by calling the <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a><span data-ttu-id="c733e-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="c733e-104">Parameters</span></span>

- <span data-ttu-id="c733e-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="c733e-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="c733e-106">Składnik zapisywania służący do konwertowania treści komunikatu na ciąg.</span><span class="sxs-lookup"><span data-stu-id="c733e-106">The writer that is used to convert the message body to a string.</span></span>

## <a name="remarks"></a><span data-ttu-id="c733e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c733e-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="c733e-108">Metoda `Message.BodyToString` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c733e-108">The `Message.BodyToString` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="c733e-109">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="c733e-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c733e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c733e-110">Requirements</span></span>

<span data-ttu-id="c733e-111">**Przestrzeń nazw:** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="c733e-111">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="c733e-112">**Zestaw:** System. ServiceModel. dll</span><span class="sxs-lookup"><span data-stu-id="c733e-112">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="c733e-113">**.NET Framework wersje:** Dostępne od 3,0.</span><span class="sxs-lookup"><span data-stu-id="c733e-113">**.NET Framework versions:** Available since 3.0.</span></span>
