---
title: Wyliczenie CorDebugCodeInvokeKind
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fa8de1a561e59e00d5bd9e78172d78b417aeff0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951964"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="4452a-102">Wyliczenie CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="4452a-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="4452a-103">Opisuje sposób, w jaki wyeksportowana funkcja wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="4452a-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4452a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4452a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="4452a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4452a-105">Members</span></span>  
  
|<span data-ttu-id="4452a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4452a-106">Member</span></span>|<span data-ttu-id="4452a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4452a-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="4452a-108">Jeśli jakikolwiek kod zarządzany jest wywoływany przez tę metodę, będzie musiał znajdować się w nim jawne zdarzenia lub punkty przerwania.</span><span class="sxs-lookup"><span data-stu-id="4452a-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="4452a-109">--lub--</span><span class="sxs-lookup"><span data-stu-id="4452a-109">--or--</span></span><br /><br /> <span data-ttu-id="4452a-110">Możemy po prostu zrezygnować z kodu zarządzanego ta metoda wywołuje, ponieważ nie ma prostego sposobu na jej zatrzymanie.</span><span class="sxs-lookup"><span data-stu-id="4452a-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="4452a-111">--lub--</span><span class="sxs-lookup"><span data-stu-id="4452a-111">--or--</span></span><br /><br /> <span data-ttu-id="4452a-112">Metoda może nigdy nie wywołać kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="4452a-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="4452a-113">Ta metoda wywoła kod zarządzany za pośrednictwem instrukcji return.</span><span class="sxs-lookup"><span data-stu-id="4452a-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="4452a-114">Należy wzważyć przy następnym zarządzanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4452a-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="4452a-115">Ta metoda wywoła kod zarządzany za pośrednictwem wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="4452a-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="4452a-116">Wykonywanie pojedynczych instrukcji wywołania i przechodzenie do nich powinno dotrzeć do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="4452a-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4452a-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4452a-117">Remarks</span></span>  
 <span data-ttu-id="4452a-118">To wyliczenie jest używane przez metodę [Metoda ICorDebugProcess6:: GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) w celu uzyskania informacji na temat wykonywania kroków w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="4452a-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4452a-119">To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4452a-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4452a-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4452a-120">Requirements</span></span>  
 <span data-ttu-id="4452a-121">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4452a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4452a-122">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4452a-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4452a-123">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4452a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4452a-124">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4452a-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4452a-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4452a-125">See also</span></span>

- [<span data-ttu-id="4452a-126">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4452a-126">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="4452a-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4452a-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
