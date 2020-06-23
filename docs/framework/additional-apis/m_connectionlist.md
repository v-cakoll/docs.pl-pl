---
title: Connection. m_ConnectionList — pole
description: Dowiedz się więcej o polu Connection. m_ConnectionList w programie .NET, który zawiera obiekty połączeń obsługujące ten sam identyfikator URI i wartości udziałów dla innych właściwości.
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
ms.openlocfilehash: 478b2441c062e8df6f4e718bd66d7af329f20f12
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989721"
---
# <a name="connectiongroupm_connectionlist-field"></a><span data-ttu-id="84874-103">Connections. m — \_ pole ConnectionList</span><span class="sxs-lookup"><span data-stu-id="84874-103">ConnectionGroup.m\_ConnectionList Field</span></span>

<span data-ttu-id="84874-104">`ConnectionGroup.m_ConnectionList`jest <xref:System.Collections.ArrayList> obiektem połączenia, który służy do tego samego identyfikatora URI i udostępnia te same wartości dla innych właściwości, takich jak wygaśnięcie i uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="84874-104">`ConnectionGroup.m_ConnectionList` is an <xref:System.Collections.ArrayList> of connection objects that serves the same URI and share the same values for some other properties like expiration and authentication.</span></span>

## <a name="syntax"></a><span data-ttu-id="84874-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="84874-105">Syntax</span></span>
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> <span data-ttu-id="84874-106">`ConnectionGroup.m_ConnectionList`Pole jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="84874-106">The `ConnectionGroup.m_ConnectionList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="84874-107">Firma Microsoft nie obsługuje korzystania z tego pola w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="84874-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="84874-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84874-108">Requirements</span></span>

<span data-ttu-id="84874-109">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="84874-109">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="84874-110">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="84874-110">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="84874-111">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="84874-111">**.NET Framework versions:** Available since 2.0.</span></span>
