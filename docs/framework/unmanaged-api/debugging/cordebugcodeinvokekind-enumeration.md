---
title: Wyliczenie CorDebugCodeInvokeKind
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugCodeInvokeKind
api_location: mscordbi.dll
api_type: COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10b45938cfe63fa98fdb06bc20c66cc0f25c41a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="8f584-102">Wyliczenie CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="8f584-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="8f584-103">W tym artykule opisano, jak wyeksportowanej funkcji wywołuje kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8f584-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f584-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f584-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="8f584-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8f584-105">Members</span></span>  
  
|<span data-ttu-id="8f584-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8f584-106">Member</span></span>|<span data-ttu-id="8f584-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8f584-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="8f584-108">Jeśli dowolny kod zarządzany jest wywoływany przez tę metodę, będzie musiał znajdować się później przez jawne zdarzenia lub punktów przerwania.</span><span class="sxs-lookup"><span data-stu-id="8f584-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="8f584-109">--lub--</span><span class="sxs-lookup"><span data-stu-id="8f584-109">--or--</span></span><br /><br /> <span data-ttu-id="8f584-110">Firma Microsoft może po prostu nie niektóre z kodu zarządzanego, wywołania tej metody, ponieważ nie istnieje łatwy sposób można zatrzymać na nim.</span><span class="sxs-lookup"><span data-stu-id="8f584-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="8f584-111">--lub--</span><span class="sxs-lookup"><span data-stu-id="8f584-111">--or--</span></span><br /><br /> <span data-ttu-id="8f584-112">Metoda nigdy nie mogą wywoływać kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8f584-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="8f584-113">Ta metoda wywoła kodu zarządzanego za pośrednictwem instrukcji return.</span><span class="sxs-lookup"><span data-stu-id="8f584-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="8f584-114">Wykonywanie krok po kroku, powinien przyjeździe kolejnego kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8f584-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="8f584-115">Ta metoda wywoła kodu zarządzanego za pośrednictwem wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="8f584-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="8f584-116">Krokowe wykonywanie jednego i pominięcie żadnego wywołania instrukcje powinny przyjeździe kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8f584-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f584-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f584-117">Remarks</span></span>  
 <span data-ttu-id="8f584-118">To wyliczenie jest używany przez [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metody, aby podać informacje o krokowe wykonywanie kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8f584-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f584-119">To wyliczenie jest przeznaczona do użycia w platformę .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="8f584-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f584-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f584-120">Requirements</span></span>  
 <span data-ttu-id="8f584-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f584-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f584-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f584-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f584-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f584-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f584-124">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f584-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f584-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f584-125">See Also</span></span>  
 [<span data-ttu-id="8f584-126">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8f584-126">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="8f584-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8f584-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
