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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b5de58caeeac5ae85402e91a1402958e68336bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967595"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="abadb-102">Wyliczenie CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="abadb-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="abadb-103">Opisuje, dlaczego wyeksportowana funkcja wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="abadb-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abadb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="abadb-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="abadb-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="abadb-105">Members</span></span>  
  
|<span data-ttu-id="abadb-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="abadb-106">Member</span></span>|<span data-ttu-id="abadb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="abadb-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="abadb-108">Brak lub nieznany.</span><span class="sxs-lookup"><span data-stu-id="abadb-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="abadb-109">Kod zarządzany będzie uruchamiał każdy zarządzany punkt wejścia, taki jak odwrotne wywołanie p.</span><span class="sxs-lookup"><span data-stu-id="abadb-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="abadb-110">Każdy bardziej szczegółowy cel jest nieznany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="abadb-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="abadb-111">Kod zarządzany będzie uruchamiał Konstruktor statyczny.</span><span class="sxs-lookup"><span data-stu-id="abadb-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="abadb-112">Kod zarządzany uruchomi implementację dla pewnej metody interfejsu, która została wywołana.</span><span class="sxs-lookup"><span data-stu-id="abadb-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abadb-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="abadb-113">Remarks</span></span>  
 <span data-ttu-id="abadb-114">To wyliczenie jest używane przez metodę [Metoda ICorDebugProcess6:: GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) w celu uzyskania informacji na temat wykonywania kroków w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="abadb-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abadb-115">To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania .NET Native.</span><span class="sxs-lookup"><span data-stu-id="abadb-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abadb-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abadb-116">Requirements</span></span>  
 <span data-ttu-id="abadb-117">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abadb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abadb-118">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abadb-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abadb-119">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abadb-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abadb-120">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abadb-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abadb-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abadb-121">See also</span></span>

- [<span data-ttu-id="abadb-122">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="abadb-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="abadb-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="abadb-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
