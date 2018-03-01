---
title: Wyliczenie CorDebugCodeInvokePurpose
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
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e87e5d8baf3ff7c87efe8f6bd96f8fd806527363
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="901a2-102">Wyliczenie CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="901a2-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="901a2-103">Opisuje, dlaczego wyeksportowanej funkcji wywołania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="901a2-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="901a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="901a2-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="901a2-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="901a2-105">Members</span></span>  
  
|<span data-ttu-id="901a2-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="901a2-106">Member</span></span>|<span data-ttu-id="901a2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="901a2-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="901a2-108">Brak lub nieznany.</span><span class="sxs-lookup"><span data-stu-id="901a2-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="901a2-109">Zarządzany kod uruchomi żadnych zarządzany punkt wejścia, np. odwrotna p-invoke.</span><span class="sxs-lookup"><span data-stu-id="901a2-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="901a2-110">Wszelkie bardziej szczegółowe celem jest nieznany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="901a2-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="901a2-111">Zarządzany kod zostanie uruchomiony Konstruktor statyczny.</span><span class="sxs-lookup"><span data-stu-id="901a2-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="901a2-112">Zarządzany kod zostanie uruchomiony implementację niektóre metody interfejsu, która została wywołana.</span><span class="sxs-lookup"><span data-stu-id="901a2-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="901a2-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="901a2-113">Remarks</span></span>  
 <span data-ttu-id="901a2-114">To wyliczenie jest używany przez [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metody, aby podać informacje o krokowe wykonywanie kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="901a2-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="901a2-115">To wyliczenie jest przeznaczona do użycia w platformę .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="901a2-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="901a2-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="901a2-116">Requirements</span></span>  
 <span data-ttu-id="901a2-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="901a2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="901a2-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="901a2-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="901a2-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="901a2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="901a2-120">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="901a2-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="901a2-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="901a2-121">See Also</span></span>  
 [<span data-ttu-id="901a2-122">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="901a2-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="901a2-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="901a2-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
