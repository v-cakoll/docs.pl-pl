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
ms.openlocfilehash: a90ddd27834e7614c1827d606a9955b4d6c53127
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795979"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="327cc-102">Wyliczenie CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="327cc-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="327cc-103">Zawiera dodatkowe informacje na temat zdarzeń debugowania na platformie Windows.</span><span class="sxs-lookup"><span data-stu-id="327cc-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="327cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="327cc-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="327cc-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="327cc-105">Members</span></span>  
  
|<span data-ttu-id="327cc-106">Członek</span><span class="sxs-lookup"><span data-stu-id="327cc-106">Member</span></span>|<span data-ttu-id="327cc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="327cc-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="327cc-108">Wskazuje, że zdarzenie debugowania jest wyjątkiem pierwszej szansy.</span><span class="sxs-lookup"><span data-stu-id="327cc-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="327cc-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="327cc-109">Remarks</span></span>  
 <span data-ttu-id="327cc-110">Metoda [Metoda ICorDebugProcess6::D ecodeevent](icordebugprocess6-decodeevent-method.md) zawiera `dwFlags` parametr, który dostarcza dodatkowych informacji na temat zdarzenia debugowania i którego wartość zależy od architektury docelowej.</span><span class="sxs-lookup"><span data-stu-id="327cc-110">The [ICorDebugProcess6::DecodeEvent](icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="327cc-111">`CorDebugDecodeEventFlagsWindows` Wyliczenie może być używane z zdarzeniami debugowania na platformie Windows.</span><span class="sxs-lookup"><span data-stu-id="327cc-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="327cc-112">To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania .NET Native.</span><span class="sxs-lookup"><span data-stu-id="327cc-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="327cc-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="327cc-113">Requirements</span></span>  
 <span data-ttu-id="327cc-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="327cc-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="327cc-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="327cc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="327cc-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="327cc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="327cc-117">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="327cc-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="327cc-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="327cc-118">See also</span></span>

- [<span data-ttu-id="327cc-119">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="327cc-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
