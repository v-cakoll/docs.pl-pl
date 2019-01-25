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
ms.openlocfilehash: 7d712a46a8ddb79846e56077e9ed6283ea4d40ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523886"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="ba4a4-102">Wyliczenie CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="ba4a4-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="ba4a4-103">W tym artykule opisano, jak eksportowanych funkcji wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="ba4a4-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba4a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba4a4-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="ba4a4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ba4a4-105">Members</span></span>  
  
|<span data-ttu-id="ba4a4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ba4a4-106">Member</span></span>|<span data-ttu-id="ba4a4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ba4a4-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="ba4a4-108">Jeśli żadnego kodu zarządzanego wywoływaną przez tę metodę, ma znajdować się później przez jawne zdarzenia lub punkty przerwania.</span><span class="sxs-lookup"><span data-stu-id="ba4a4-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="ba4a4-109">--lub--</span><span class="sxs-lookup"><span data-stu-id="ba4a4-109">--or--</span></span><br /><br /> <span data-ttu-id="ba4a4-110">Możemy po prostu pominąć część kodu zarządzanego, które wywołuje ta metoda, ponieważ nie istnieje łatwy sposób można zatrzymać na nim.</span><span class="sxs-lookup"><span data-stu-id="ba4a4-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="ba4a4-111">--lub--</span><span class="sxs-lookup"><span data-stu-id="ba4a4-111">--or--</span></span><br /><br /> <span data-ttu-id="ba4a4-112">Metoda nigdy nie mogą wywoływać kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="ba4a4-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="ba4a4-113">Ta metoda wywoła kodu zarządzanego za pomocą instrukcji return.</span><span class="sxs-lookup"><span data-stu-id="ba4a4-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="ba4a4-114">Przechodzenie krok po kroku, powinien pojawić się w następnym kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="ba4a4-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="ba4a4-115">Ta metoda wywoła kodu zarządzanego za pośrednictwem wywołania tail.</span><span class="sxs-lookup"><span data-stu-id="ba4a4-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="ba4a4-116">Przechodzenie z jednego i Krokowe przechodzenie przez dowolny instrukcje wywołanie powinno pojawić się w kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="ba4a4-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba4a4-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba4a4-117">Remarks</span></span>  
 <span data-ttu-id="ba4a4-118">To wyliczenie jest używane przez [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metodę w celu udostępnienia informacji na temat krokowe wykonywanie kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="ba4a4-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba4a4-119">To wyliczenie jest przeznaczona do użytku w .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="ba4a4-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba4a4-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ba4a4-120">Requirements</span></span>  
 <span data-ttu-id="ba4a4-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba4a4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba4a4-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba4a4-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba4a4-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba4a4-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba4a4-124">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba4a4-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba4a4-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba4a4-125">See also</span></span>
- [<span data-ttu-id="ba4a4-126">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ba4a4-126">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="ba4a4-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ba4a4-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
