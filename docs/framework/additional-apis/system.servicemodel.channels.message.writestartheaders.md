---
title: Message. WriteStartHeaders — Metoda (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: c826e6a3b976e5705e9815586441e8a25b64f76e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214862"
---
# <a name="messagewritestartheaders-method"></a><span data-ttu-id="f65bc-102">Message. WriteStartHeaders — Metoda</span><span class="sxs-lookup"><span data-stu-id="f65bc-102">Message.WriteStartHeaders Method</span></span>

<span data-ttu-id="f65bc-103">Zapisuje nagłówek startowy w pliku XML przez wywołanie metody <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f65bc-103">Writes the start header into an XML file by calling the <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a><span data-ttu-id="f65bc-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="f65bc-104">Parameters</span></span>

- <span data-ttu-id="f65bc-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="f65bc-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="f65bc-106">Składnik zapisywania, który jest używany do zapisywania nagłówka startowego w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="f65bc-106">The writer that is used to write the start header into an XML file.</span></span>

## <a name="remarks"></a><span data-ttu-id="f65bc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f65bc-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="f65bc-108">Metoda `Message.WriteStartHeaders` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f65bc-108">The `Message.WriteStartHeaders` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f65bc-109">Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="f65bc-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f65bc-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f65bc-110">Requirements</span></span>

<span data-ttu-id="f65bc-111">**Przestrzeń nazw:** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="f65bc-111">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="f65bc-112">**Zestaw:** System. ServiceModel. dll</span><span class="sxs-lookup"><span data-stu-id="f65bc-112">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="f65bc-113">**.NET Framework wersje:** Dostępne od 3,0.</span><span class="sxs-lookup"><span data-stu-id="f65bc-113">**.NET Framework versions:** Available since 3.0.</span></span>
