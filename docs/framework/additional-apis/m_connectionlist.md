---
title: Connection. m_ConnectionList, pole
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a06e535c554f765161d619d97f2e70072fbd0d5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120019"
---
# <a name="connectiongroupm_connectionlist-field"></a><span data-ttu-id="4ed80-102">ConnectionList pole połączenia. m\_</span><span class="sxs-lookup"><span data-stu-id="4ed80-102">ConnectionGroup.m\_ConnectionList Field</span></span>

<span data-ttu-id="4ed80-103">`ConnectionGroup.m_ConnectionList` to <xref:System.Collections.ArrayList> obiektów połączeń, które obsługują ten sam identyfikator URI i mają te same wartości dla niektórych innych właściwości, takich jak wygaśnięcie i uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="4ed80-103">`ConnectionGroup.m_ConnectionList` is an <xref:System.Collections.ArrayList> of connection objects that serves the same URI and share the same values for some other properties like expiration and authentication.</span></span>

## <a name="syntax"></a><span data-ttu-id="4ed80-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ed80-104">Syntax</span></span>
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> <span data-ttu-id="4ed80-105">Pole `ConnectionGroup.m_ConnectionList` jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4ed80-105">The `ConnectionGroup.m_ConnectionList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="4ed80-106">Firma Microsoft nie obsługuje korzystania z tego pola w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="4ed80-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="4ed80-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ed80-107">Requirements</span></span>

<span data-ttu-id="4ed80-108">**Przestrzeń nazw:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="4ed80-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="4ed80-109">**Zestaw:** System (w pliku System. dll)</span><span class="sxs-lookup"><span data-stu-id="4ed80-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="4ed80-110">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="4ed80-110">**.NET Framework versions:** Available since 2.0.</span></span>
