---
title: Pole ConnectionGroup.m_ConnectionList
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup.m_ConnectionList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 186083cf-8dff-4600-a2ab-6fed4b4de6af
ms.openlocfilehash: 8eb6f215c36e214f7095eeba90bf0aed66dfcea0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155853"
---
# <a name="connectiongroupm_connectionlist-field"></a><span data-ttu-id="53e64-102">Pole ConnectionGroup.m\_ConnectionList</span><span class="sxs-lookup"><span data-stu-id="53e64-102">ConnectionGroup.m\_ConnectionList Field</span></span>

<span data-ttu-id="53e64-103">`ConnectionGroup.m_ConnectionList`jest <xref:System.Collections.ArrayList> obiektem połączenia, który obsługuje ten sam identyfikator URI i współużytkuje te same wartości dla niektórych innych właściwości, takich jak wygaśnięcie i uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="53e64-103">`ConnectionGroup.m_ConnectionList` is an <xref:System.Collections.ArrayList> of connection objects that serves the same URI and share the same values for some other properties like expiration and authentication.</span></span>

## <a name="syntax"></a><span data-ttu-id="53e64-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53e64-104">Syntax</span></span>
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> <span data-ttu-id="53e64-105">To `ConnectionGroup.m_ConnectionList` pole jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="53e64-105">The `ConnectionGroup.m_ConnectionList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="53e64-106">Firma Microsoft w żadnym wypadku nie obsługuje używania tego pola w aplikacji produkcyjnej.</span><span class="sxs-lookup"><span data-stu-id="53e64-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="53e64-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53e64-107">Requirements</span></span>

<span data-ttu-id="53e64-108">**Obszar nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="53e64-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="53e64-109">**Montaż:** System (w pliku System.dll)</span><span class="sxs-lookup"><span data-stu-id="53e64-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="53e64-110">**Wersje programu .NET Framework:** Dostępne od 2.0.</span><span class="sxs-lookup"><span data-stu-id="53e64-110">**.NET Framework versions:** Available since 2.0.</span></span>
