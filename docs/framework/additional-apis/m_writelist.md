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
author: guardrex
ms.author: mairaw
ms.openlocfilehash: a7446b9cbbfd4d3a4d38368a8e24c99527cf9108
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146709"
---
# <a name="connectionmwritelist-field"></a><span data-ttu-id="64f9a-102">Connection.m\_WriteList pola</span><span class="sxs-lookup"><span data-stu-id="64f9a-102">Connection.m\_WriteList Field</span></span>

<span data-ttu-id="64f9a-103">`Connection.m_WriteList` jest <xref:System.Collections.ArrayList> z <xref:System.Net.HttpWebRequest> obiektów, które są umieszczone w kolejce do wysłania za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="64f9a-103">`Connection.m_WriteList` is an <xref:System.Collections.ArrayList> of <xref:System.Net.HttpWebRequest> objects that are queued up to be sent over HTTP.</span></span>

## <a name="syntax"></a><span data-ttu-id="64f9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="64f9a-104">Syntax</span></span>
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> <span data-ttu-id="64f9a-105">`Connection.m_WriteList` Pole jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="64f9a-105">The `Connection.m_WriteList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="64f9a-106">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="64f9a-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="64f9a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="64f9a-107">Requirements</span></span>

<span data-ttu-id="64f9a-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="64f9a-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="64f9a-109">**Zestaw:** System (System.dll)</span><span class="sxs-lookup"><span data-stu-id="64f9a-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="64f9a-110">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="64f9a-110">**.NET Framework versions:** Available since 2.0.</span></span>
