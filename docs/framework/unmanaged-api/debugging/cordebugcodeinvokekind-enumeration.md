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
ms.openlocfilehash: 54332f5b3383f1c1513242a79cbd81eb8aa5c4f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179261"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="262bd-102">Wyliczenie CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="262bd-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="262bd-103">W tym artykule opisano, jak wyeksportowana funkcja wywołuje kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="262bd-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="262bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="262bd-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,
    CODE_INVOKE_KIND_RETURN,
    CODE_INVOKE_KIND_TAILCALL,
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="262bd-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="262bd-105">Members</span></span>  
  
|<span data-ttu-id="262bd-106">Członek</span><span class="sxs-lookup"><span data-stu-id="262bd-106">Member</span></span>|<span data-ttu-id="262bd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="262bd-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="262bd-108">Jeśli dowolny kod zarządzany jest wywoływany przez tę metodę, będzie musiał znajdować się przez jawne zdarzenia lub punkty przerwania później.</span><span class="sxs-lookup"><span data-stu-id="262bd-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="262bd-109">--lub--</span><span class="sxs-lookup"><span data-stu-id="262bd-109">--or--</span></span><br /><br /> <span data-ttu-id="262bd-110">Możemy po prostu pominąć niektóre kod zarządzany tej metody wywołuje, ponieważ nie ma łatwego sposobu, aby zatrzymać się na nim.</span><span class="sxs-lookup"><span data-stu-id="262bd-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="262bd-111">--lub--</span><span class="sxs-lookup"><span data-stu-id="262bd-111">--or--</span></span><br /><br /> <span data-ttu-id="262bd-112">Metoda nigdy nie może wywołać kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="262bd-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="262bd-113">Ta metoda wywoła kod zarządzany za pomocą instrukcji zwracania.</span><span class="sxs-lookup"><span data-stu-id="262bd-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="262bd-114">Wychodząc powinien dotrzeć do następnego kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="262bd-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="262bd-115">Ta metoda będzie wywoływać kod zarządzany za pośrednictwem wywołania ogona.</span><span class="sxs-lookup"><span data-stu-id="262bd-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="262bd-116">Pojedynczy krok po kroku i przechodzenie przez wszelkie instrukcje wywołania powinny uzyskać kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="262bd-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="262bd-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="262bd-117">Remarks</span></span>  
 <span data-ttu-id="262bd-118">To wyliczenie jest używane przez [metodę ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) w celu zapewnienia informacji o przechodzeniu przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="262bd-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="262bd-119">To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania natywnego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="262bd-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="262bd-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="262bd-120">Requirements</span></span>  
 <span data-ttu-id="262bd-121">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="262bd-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="262bd-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="262bd-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="262bd-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="262bd-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="262bd-124">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="262bd-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="262bd-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="262bd-125">See also</span></span>

- [<span data-ttu-id="262bd-126">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="262bd-126">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="262bd-127">Debugging</span><span class="sxs-lookup"><span data-stu-id="262bd-127">Debugging</span></span>](index.md)
