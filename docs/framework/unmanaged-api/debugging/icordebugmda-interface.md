---
title: ICorDebugMDA — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
ms.openlocfilehash: 4201fe23bf54388510088e21471edce91809e94c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129799"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="c05cb-102">ICorDebugMDA — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c05cb-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="c05cb-103">Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="c05cb-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c05cb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c05cb-104">Methods</span></span>  
  
|<span data-ttu-id="c05cb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c05cb-105">Method</span></span>|<span data-ttu-id="c05cb-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c05cb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c05cb-107">GetDescription, metoda</span><span class="sxs-lookup"><span data-stu-id="c05cb-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="c05cb-108">Pobiera ciąg zawierający opis tego elementu MDA.</span><span class="sxs-lookup"><span data-stu-id="c05cb-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="c05cb-109">GetFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="c05cb-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="c05cb-110">Pobiera flagi skojarzone z tym zdarzeniem MDA.</span><span class="sxs-lookup"><span data-stu-id="c05cb-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="c05cb-111">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="c05cb-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="c05cb-112">Pobiera ciąg zawierający nazwę tego elementu MDA.</span><span class="sxs-lookup"><span data-stu-id="c05cb-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="c05cb-113">GetOSThreadId, metoda</span><span class="sxs-lookup"><span data-stu-id="c05cb-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="c05cb-114">Pobiera identyfikator wątku systemu operacyjnego, na którym jest wykonywane zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="c05cb-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="c05cb-115">GetXML, metoda</span><span class="sxs-lookup"><span data-stu-id="c05cb-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="c05cb-116">Pobiera pełny strumień XML skojarzony z tym MDA.</span><span class="sxs-lookup"><span data-stu-id="c05cb-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c05cb-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c05cb-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c05cb-118">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="c05cb-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c05cb-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c05cb-119">Requirements</span></span>  
 <span data-ttu-id="c05cb-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c05cb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c05cb-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c05cb-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c05cb-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c05cb-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c05cb-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c05cb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05cb-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c05cb-124">See also</span></span>

- [<span data-ttu-id="c05cb-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c05cb-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c05cb-126">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="c05cb-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
