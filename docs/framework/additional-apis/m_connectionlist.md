---
title: ConnectionGroup.m_ConnectionList Field
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
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d06968c844dc9187b973af156a29ded9ba7cde66
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301397"
---
# <a name="connectiongroupmconnectionlist-field"></a><span data-ttu-id="e8fef-102">ConnectionGroup.m\_ConnectionList Field</span><span class="sxs-lookup"><span data-stu-id="e8fef-102">ConnectionGroup.m\_ConnectionList Field</span></span>

<span data-ttu-id="e8fef-103">`ConnectionGroup.m_ConnectionList` jest <xref:System.Collections.ArrayList> obiektów połączeń, które służy do tego samego udziału i identyfikator URI takie same wartości dla niektórych innych właściwości, takich jak uwierzytelnianie i wygaśnięcia.</span><span class="sxs-lookup"><span data-stu-id="e8fef-103">`ConnectionGroup.m_ConnectionList` is an <xref:System.Collections.ArrayList> of connection objects that serves the same URI and share the same values for some other properties like expiration and authentication.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8fef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8fef-104">Syntax</span></span>
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> <span data-ttu-id="e8fef-105">`ConnectionGroup.m_ConnectionList` Pole jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e8fef-105">The `ConnectionGroup.m_ConnectionList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="e8fef-106">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="e8fef-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8fef-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8fef-107">Requirements</span></span>

<span data-ttu-id="e8fef-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="e8fef-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="e8fef-109">**Zestaw:** System (System.dll)</span><span class="sxs-lookup"><span data-stu-id="e8fef-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="e8fef-110">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="e8fef-110">**.NET Framework versions:** Available since 2.0.</span></span>
