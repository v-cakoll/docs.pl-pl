---
title: NOTIFY_FILTER — Wyliczenie
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98c3e1ed3da209cbded5d76d938d2420fce606be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431021"
---
# <a name="notifyfilter-enumeration"></a><span data-ttu-id="d6f7c-102">NOTIFY_FILTER — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d6f7c-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="d6f7c-103">Identyfikuje wywołań zwrotnych dla funkcji debugera.</span><span class="sxs-lookup"><span data-stu-id="d6f7c-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="d6f7c-104">Aby uzyskać więcej informacji, zobacz [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d6f7c-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6f7c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6f7c-105">Syntax</span></span>  
  
```  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a><span data-ttu-id="d6f7c-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d6f7c-106">Members</span></span>  
  
|<span data-ttu-id="d6f7c-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d6f7c-107">Member</span></span>|<span data-ttu-id="d6f7c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="d6f7c-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="d6f7c-109">Oznacza to, że [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) powinna być wywoływana metoda.</span><span class="sxs-lookup"><span data-stu-id="d6f7c-109">Indicates that the [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="d6f7c-110">Oznacza to, że [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) powinna być wywoływana metoda.</span><span class="sxs-lookup"><span data-stu-id="d6f7c-110">Indicates that the [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="d6f7c-111">Oznacza to, że [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) powinna być wywoływana metoda.</span><span class="sxs-lookup"><span data-stu-id="d6f7c-111">Indicates that the [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="d6f7c-112">Oznacza to, że [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) powinna być wywoływana metoda.</span><span class="sxs-lookup"><span data-stu-id="d6f7c-112">Indicates that the [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="d6f7c-113">Oznacza to, że wszystkie [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) można wywołać metody.</span><span class="sxs-lookup"><span data-stu-id="d6f7c-113">Indicates that all of the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="d6f7c-114">Aktywuje wszystkie istniejącymi i przyszłymi powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="d6f7c-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="d6f7c-115">Wskazuje, powinna być wywoływana żadna metoda powiadomień.</span><span class="sxs-lookup"><span data-stu-id="d6f7c-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6f7c-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6f7c-116">Requirements</span></span>  
 <span data-ttu-id="d6f7c-117">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="d6f7c-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6f7c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6f7c-118">See Also</span></span>  
 [<span data-ttu-id="d6f7c-119">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="d6f7c-119">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
