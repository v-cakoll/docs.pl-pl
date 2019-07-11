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
ms.openlocfilehash: 09c36dd65c8a4202f13d362668f74cd9a362e35a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744357"
---
# <a name="notifyfilter-enumeration"></a><span data-ttu-id="e4caa-102">NOTIFY_FILTER — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e4caa-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="e4caa-103">Identyfikuje wywołań zwrotnych debugera funkcji.</span><span class="sxs-lookup"><span data-stu-id="e4caa-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="e4caa-104">Aby uzyskać więcej informacji, zobacz [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e4caa-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4caa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4caa-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="e4caa-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e4caa-106">Members</span></span>  
  
|<span data-ttu-id="e4caa-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e4caa-107">Member</span></span>|<span data-ttu-id="e4caa-108">Opis</span><span class="sxs-lookup"><span data-stu-id="e4caa-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="e4caa-109">Oznacza to, że [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) powinna ona zostać wywołana metoda.</span><span class="sxs-lookup"><span data-stu-id="e4caa-109">Indicates that the [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="e4caa-110">Oznacza to, że [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) powinna ona zostać wywołana metoda.</span><span class="sxs-lookup"><span data-stu-id="e4caa-110">Indicates that the [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="e4caa-111">Oznacza to, że [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) powinna ona zostać wywołana metoda.</span><span class="sxs-lookup"><span data-stu-id="e4caa-111">Indicates that the [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="e4caa-112">Oznacza to, że [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) powinna ona zostać wywołana metoda.</span><span class="sxs-lookup"><span data-stu-id="e4caa-112">Indicates that the [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="e4caa-113">Oznacza to, że wszystkie [inotifysink2 —](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) metody powinna ona zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="e4caa-113">Indicates that all of the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="e4caa-114">Aktywuje wszystkich istniejących i przyszłych powiadomień.</span><span class="sxs-lookup"><span data-stu-id="e4caa-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="e4caa-115">Wskazuje, czy można wywołać metody nie powiadamiania.</span><span class="sxs-lookup"><span data-stu-id="e4caa-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4caa-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4caa-116">Requirements</span></span>  
 <span data-ttu-id="e4caa-117">**Nagłówek:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="e4caa-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4caa-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4caa-118">See also</span></span>

- [<span data-ttu-id="e4caa-119">Wyliczenia magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="e4caa-119">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
