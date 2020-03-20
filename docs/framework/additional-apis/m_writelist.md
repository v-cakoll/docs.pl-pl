---
title: Pole Connection.m_WriteList
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
ms.openlocfilehash: 6c60831ddf23ce8ac9afcf244383d24732c3ef8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155840"
---
# <a name="connectionm_writelist-field"></a><span data-ttu-id="f9460-102">Pole Lista\_zapisów Connection.m</span><span class="sxs-lookup"><span data-stu-id="f9460-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="f9460-103">`Connection.m_WriteList`jest <xref:System.Collections.ArrayList> obiektem, <xref:System.Net.HttpWebRequest> które są umieszczane w kolejce do wysłania za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f9460-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="f9460-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9460-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="f9460-105">To `Connection.m_WriteList` pole jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f9460-105">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f9460-106">Firma Microsoft w żadnym wypadku nie obsługuje używania tego pola w aplikacji produkcyjnej.</span><span class="sxs-lookup"><span data-stu-id="f9460-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9460-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9460-107">Requirements</span></span>

<span data-ttu-id="f9460-108">**Obszar nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="f9460-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="f9460-109">**Montaż:** System (w pliku System.dll)</span><span class="sxs-lookup"><span data-stu-id="f9460-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="f9460-110">**Wersje programu .NET Framework:** Dostępne od 2.0.</span><span class="sxs-lookup"><span data-stu-id="f9460-110">**.NET Framework versions:** Available since 2.0.</span></span>
