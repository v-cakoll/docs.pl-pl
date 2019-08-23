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
ms.openlocfilehash: ec23e0f272852088987fcc74767d3645778eab45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955682"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="d463b-102">Wyliczenie CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="d463b-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="d463b-103">Zawiera dodatkowe informacje na temat zdarzeń debugowania na platformie Windows.</span><span class="sxs-lookup"><span data-stu-id="d463b-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d463b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d463b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="d463b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d463b-105">Members</span></span>  
  
|<span data-ttu-id="d463b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d463b-106">Member</span></span>|<span data-ttu-id="d463b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d463b-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="d463b-108">Wskazuje, że zdarzenie debugowania jest wyjątkiem pierwszej szansy.</span><span class="sxs-lookup"><span data-stu-id="d463b-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d463b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d463b-109">Remarks</span></span>  
 <span data-ttu-id="d463b-110">Metoda [Metoda ICorDebugProcess6::D ecodeevent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) zawiera `dwFlags` parametr, który dostarcza dodatkowych informacji na temat zdarzenia debugowania i którego wartość zależy od architektury docelowej.</span><span class="sxs-lookup"><span data-stu-id="d463b-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="d463b-111">`CorDebugDecodeEventFlagsWindows` Wyliczenie może być używane z zdarzeniami debugowania na platformie Windows.</span><span class="sxs-lookup"><span data-stu-id="d463b-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d463b-112">To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d463b-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d463b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d463b-113">Requirements</span></span>  
 <span data-ttu-id="d463b-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d463b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d463b-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d463b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d463b-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d463b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d463b-117">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d463b-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d463b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d463b-118">See also</span></span>

- [<span data-ttu-id="d463b-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d463b-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
