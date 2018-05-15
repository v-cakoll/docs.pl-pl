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
ms.openlocfilehash: 79730bb98a7e2d84517ed068a52614ad8650f541
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="a5e3e-102">Wyliczenie CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="a5e3e-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="a5e3e-103">Opisuje, dlaczego wyeksportowanej funkcji wywołania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a5e3e-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5e3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5e3e-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="a5e3e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a5e3e-105">Members</span></span>  
  
|<span data-ttu-id="a5e3e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a5e3e-106">Member</span></span>|<span data-ttu-id="a5e3e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a5e3e-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="a5e3e-108">Brak lub nieznany.</span><span class="sxs-lookup"><span data-stu-id="a5e3e-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="a5e3e-109">Zarządzany kod uruchomi żadnych zarządzany punkt wejścia, np. odwrotna p-invoke.</span><span class="sxs-lookup"><span data-stu-id="a5e3e-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="a5e3e-110">Wszelkie bardziej szczegółowe celem jest nieznany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a5e3e-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="a5e3e-111">Zarządzany kod zostanie uruchomiony Konstruktor statyczny.</span><span class="sxs-lookup"><span data-stu-id="a5e3e-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="a5e3e-112">Zarządzany kod zostanie uruchomiony implementację niektóre metody interfejsu, która została wywołana.</span><span class="sxs-lookup"><span data-stu-id="a5e3e-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5e3e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5e3e-113">Remarks</span></span>  
 <span data-ttu-id="a5e3e-114">To wyliczenie jest używany przez [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metody, aby podać informacje o krokowe wykonywanie kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a5e3e-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5e3e-115">To wyliczenie jest przeznaczona do użycia w platformę .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="a5e3e-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5e3e-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5e3e-116">Requirements</span></span>  
 <span data-ttu-id="a5e3e-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5e3e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5e3e-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5e3e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5e3e-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5e3e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5e3e-120">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5e3e-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e3e-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5e3e-121">See Also</span></span>  
 [<span data-ttu-id="a5e3e-122">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a5e3e-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="a5e3e-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="a5e3e-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
