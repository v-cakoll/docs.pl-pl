---
title: Wyliczenie CorDebugDecodeEventFlagsWindows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cbbc275fd87ab9059959c2b770060ae1e11daa9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="bd021-102">Wyliczenie CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="bd021-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="bd021-103">Zawiera dodatkowe informacje o zdarzeniach debugowania na platformie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bd021-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd021-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd021-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="bd021-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bd021-105">Members</span></span>  
  
|<span data-ttu-id="bd021-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="bd021-106">Member</span></span>|<span data-ttu-id="bd021-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bd021-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="bd021-108">Wskazuje, że zdarzenie debugowania jest wyjątkach pierwszej szansy.</span><span class="sxs-lookup"><span data-stu-id="bd021-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd021-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd021-109">Remarks</span></span>  
 <span data-ttu-id="bd021-110">[ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metoda zawiera `dwFlags` parametr, który udostępnia dodatkowe informacje dotyczące zdarzenia debugowania, którego wartość jest zależna od architektury docelowej.</span><span class="sxs-lookup"><span data-stu-id="bd021-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="bd021-111">`CorDebugDecodeEventFlagsWindows` Wyliczenia mogą być używane z zdarzeń debugowania na platformie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bd021-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd021-112">To wyliczenie jest przeznaczona do użycia w platformę .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="bd021-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd021-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd021-113">Requirements</span></span>  
 <span data-ttu-id="bd021-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd021-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd021-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd021-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd021-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd021-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd021-117">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd021-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd021-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd021-118">See Also</span></span>  
 [<span data-ttu-id="bd021-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="bd021-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
