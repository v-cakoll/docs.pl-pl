---
title: "INotifySource2::SetNotifyFilter — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySource2.SetNotifyFilter
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c10b8ca9a49503b11e660a150e02ad59797664d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="f9b67-102">INotifySource2::SetNotifyFilter — Metoda</span><span class="sxs-lookup"><span data-stu-id="f9b67-102">INotifySource2::SetNotifyFilter Method</span></span>
<span data-ttu-id="f9b67-103">Przypisuje filtr powiadomień do użycia z tym źródłem.</span><span class="sxs-lookup"><span data-stu-id="f9b67-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9b67-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9b67-104">Syntax</span></span>  
  
```  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9b67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9b67-105">Parameters</span></span>  
 `in_NotifyFilter`  
 <span data-ttu-id="f9b67-106">[in] Bitowe połączenie [NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) wartości wyliczenia, które identyfikują wywołań zwrotnych dla debugera interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="f9b67-106">[in] A bitwise combination of the [NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="f9b67-107">[in] Wskaźnik do [USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) struktura, która identyfikuje wątków w debugerze interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="f9b67-107">[in] A pointer to a [USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9b67-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f9b67-108">Return Value</span></span>  
 <span data-ttu-id="f9b67-109">Wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f9b67-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9b67-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9b67-110">Requirements</span></span>  
 <span data-ttu-id="f9b67-111">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="f9b67-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b67-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9b67-112">See Also</span></span>  
 [<span data-ttu-id="f9b67-113">INotifySource2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="f9b67-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="f9b67-114">INotifyConnection2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="f9b67-114">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="f9b67-115">INotifySink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="f9b67-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
