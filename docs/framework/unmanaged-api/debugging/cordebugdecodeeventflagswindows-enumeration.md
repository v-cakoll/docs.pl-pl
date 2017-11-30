---
title: Wyliczenie CorDebugDecodeEventFlagsWindows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugDecodeEventFlagsWindows
api_location: mscordbi.dll
api_type: COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: facde76ec24d90795de7dfb70bfe5772a6f21531
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="2b29d-102">Wyliczenie CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="2b29d-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="2b29d-103">Zawiera dodatkowe informacje o zdarzeniach debugowania na platformie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2b29d-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b29d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b29d-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="2b29d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2b29d-105">Members</span></span>  
  
|<span data-ttu-id="2b29d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2b29d-106">Member</span></span>|<span data-ttu-id="2b29d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2b29d-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="2b29d-108">Wskazuje, że zdarzenie debugowania jest wyjątkach pierwszej szansy.</span><span class="sxs-lookup"><span data-stu-id="2b29d-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b29d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b29d-109">Remarks</span></span>  
 <span data-ttu-id="2b29d-110">[ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metoda zawiera `dwFlags` parametr, który udostępnia dodatkowe informacje dotyczące zdarzenia debugowania, którego wartość jest zależna od architektury docelowej.</span><span class="sxs-lookup"><span data-stu-id="2b29d-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="2b29d-111">`CorDebugDecodeEventFlagsWindows` Wyliczenia mogą być używane z zdarzeń debugowania na platformie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2b29d-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b29d-112">To wyliczenie jest przeznaczona do użycia w platformę .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="2b29d-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b29d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b29d-113">Requirements</span></span>  
 <span data-ttu-id="2b29d-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b29d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b29d-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b29d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b29d-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b29d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b29d-117">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b29d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b29d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b29d-118">See Also</span></span>  
 [<span data-ttu-id="2b29d-119">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2b29d-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
