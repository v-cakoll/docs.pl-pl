---
title: Wyliczenie CorDebugCodeInvokePurpose
ms.date: 03/30/2017
api_name:
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
ms.openlocfilehash: f1d4a1e08a63665a532c7aa3572f1e3f9c106ba6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179240"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="22ba2-102">Wyliczenie CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="22ba2-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="22ba2-103">Opisuje, dlaczego wyeksportowana funkcja wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="22ba2-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22ba2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22ba2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="22ba2-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="22ba2-105">Members</span></span>  
  
|<span data-ttu-id="22ba2-106">Członek</span><span class="sxs-lookup"><span data-stu-id="22ba2-106">Member</span></span>|<span data-ttu-id="22ba2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="22ba2-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="22ba2-108">Brak lub nieznany.</span><span class="sxs-lookup"><span data-stu-id="22ba2-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="22ba2-109">Kod zarządzany uruchomi dowolny zarządzany punkt wejścia, taki jak reverse p-invoke.</span><span class="sxs-lookup"><span data-stu-id="22ba2-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="22ba2-110">Każdy bardziej szczegółowy cel jest nieznany przez środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="22ba2-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="22ba2-111">Kod zarządzany uruchomi konstruktora statycznego.</span><span class="sxs-lookup"><span data-stu-id="22ba2-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="22ba2-112">Kod zarządzany uruchomi implementację dla niektórych metod interfejsu, który został wywołany.</span><span class="sxs-lookup"><span data-stu-id="22ba2-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22ba2-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22ba2-113">Remarks</span></span>  
 <span data-ttu-id="22ba2-114">To wyliczenie jest używane przez [metodę ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) w celu zapewnienia informacji o przechodzeniu przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="22ba2-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22ba2-115">To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania natywnego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="22ba2-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22ba2-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22ba2-116">Requirements</span></span>  
 <span data-ttu-id="22ba2-117">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22ba2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22ba2-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22ba2-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22ba2-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22ba2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22ba2-120">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22ba2-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ba2-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22ba2-121">See also</span></span>

- [<span data-ttu-id="22ba2-122">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="22ba2-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="22ba2-123">Debugging</span><span class="sxs-lookup"><span data-stu-id="22ba2-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
