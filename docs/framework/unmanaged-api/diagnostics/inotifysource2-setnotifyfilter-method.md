---
title: INotifySource2::SetNotifyFilter — Metoda
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 7ba9f68e102696da107b5cb782c76cb55ed95ee6
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441971"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="33a37-102">INotifySource2::SetNotifyFilter — Metoda</span><span class="sxs-lookup"><span data-stu-id="33a37-102">INotifySource2::SetNotifyFilter Method</span></span>
<span data-ttu-id="33a37-103">Przypisuje filtr powiadomień do użycia z tym źródłem.</span><span class="sxs-lookup"><span data-stu-id="33a37-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33a37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33a37-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33a37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33a37-105">Parameters</span></span>  
 `in_NotifyFilter`  
 <span data-ttu-id="33a37-106">podczas Bitowa kombinacja [NOTIFY_FILTER](notify-filter-enumeration.md) wartości wyliczenia, które identyfikują wywołania zwrotne dla interfejsu API debugera.</span><span class="sxs-lookup"><span data-stu-id="33a37-106">[in] A bitwise combination of the [NOTIFY_FILTER](notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="33a37-107">podczas Wskaźnik do struktury [USER_THREAD](user-thread-structure.md) , który identyfikuje wątki dla interfejsu API debugera.</span><span class="sxs-lookup"><span data-stu-id="33a37-107">[in] A pointer to a [USER_THREAD](user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33a37-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="33a37-108">Return Value</span></span>  
 <span data-ttu-id="33a37-109">S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="33a37-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33a37-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33a37-110">Requirements</span></span>  
 <span data-ttu-id="33a37-111">**Nagłówek:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="33a37-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a37-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33a37-112">See also</span></span>

- [<span data-ttu-id="33a37-113">INotifySource2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="33a37-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="33a37-114">INotifyConnection2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="33a37-114">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="33a37-115">INotifySink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="33a37-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
