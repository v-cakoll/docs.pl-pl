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
ms.openlocfilehash: 858dfe9b15422680a261fef9e22d8c89d9d7fe45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609145"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="b5e74-102">Wyliczenie CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="b5e74-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="b5e74-103">W tym artykule opisano, dlaczego eksportowanych funkcji wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="b5e74-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5e74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5e74-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="b5e74-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b5e74-105">Members</span></span>  
  
|<span data-ttu-id="b5e74-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b5e74-106">Member</span></span>|<span data-ttu-id="b5e74-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b5e74-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="b5e74-108">Brak lub nieznany.</span><span class="sxs-lookup"><span data-stu-id="b5e74-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="b5e74-109">Kod zarządzany uruchomi żadnych zarządzany punkt wejścia, takich jak p-invoke wstecznego.</span><span class="sxs-lookup"><span data-stu-id="b5e74-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="b5e74-110">Wszelkie szczegółowe celem jest nieznany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b5e74-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="b5e74-111">Zarządzany kod będzie działał Konstruktor statyczny.</span><span class="sxs-lookup"><span data-stu-id="b5e74-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="b5e74-112">Zarządzany kod będzie działał implementację dla niektórych metodę interfejsu, która została wywołana.</span><span class="sxs-lookup"><span data-stu-id="b5e74-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5e74-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5e74-113">Remarks</span></span>  
 <span data-ttu-id="b5e74-114">To wyliczenie jest używane przez [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metodę w celu udostępnienia informacji na temat krokowe wykonywanie kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b5e74-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5e74-115">To wyliczenie jest przeznaczona do użytku w .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="b5e74-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5e74-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5e74-116">Requirements</span></span>  
 <span data-ttu-id="b5e74-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5e74-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5e74-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5e74-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5e74-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5e74-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5e74-120">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5e74-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5e74-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5e74-121">See also</span></span>

- [<span data-ttu-id="b5e74-122">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b5e74-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="b5e74-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b5e74-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
