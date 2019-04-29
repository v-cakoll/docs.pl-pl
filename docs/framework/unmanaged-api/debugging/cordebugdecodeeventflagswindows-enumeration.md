---
title: Wyliczenie CorDebugDecodeEventFlagsWindows
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d4e006a03db5b16de93dfd07ec7b964db4bfc1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609220"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="c8b3e-102">Wyliczenie CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="c8b3e-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="c8b3e-103">Zawiera dodatkowe informacje na temat zdarzeń debugowania na platformie Windows.</span><span class="sxs-lookup"><span data-stu-id="c8b3e-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8b3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8b3e-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="c8b3e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c8b3e-105">Members</span></span>  
  
|<span data-ttu-id="c8b3e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c8b3e-106">Member</span></span>|<span data-ttu-id="c8b3e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c8b3e-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="c8b3e-108">Wskazuje, że zdarzenie debugowania jest wyjątku pierwszej szansy.</span><span class="sxs-lookup"><span data-stu-id="c8b3e-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8b3e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8b3e-109">Remarks</span></span>  
 <span data-ttu-id="c8b3e-110">[ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metoda zawiera `dwFlags` parametr, który zawiera dodatkowe informacje na temat zdarzeń debugowania, którego wartość jest zależny od architektury docelowej.</span><span class="sxs-lookup"><span data-stu-id="c8b3e-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="c8b3e-111">`CorDebugDecodeEventFlagsWindows` Wyliczenia mogą być używane z zdarzenia debugowania na platformie Windows.</span><span class="sxs-lookup"><span data-stu-id="c8b3e-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8b3e-112">To wyliczenie jest przeznaczona do użytku w .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="c8b3e-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8b3e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c8b3e-113">Requirements</span></span>  
 <span data-ttu-id="c8b3e-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8b3e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8b3e-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8b3e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8b3e-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8b3e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8b3e-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8b3e-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b3e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8b3e-118">See also</span></span>

- [<span data-ttu-id="c8b3e-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c8b3e-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
