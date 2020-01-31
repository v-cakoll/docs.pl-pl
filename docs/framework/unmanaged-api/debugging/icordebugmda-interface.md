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
ms.openlocfilehash: a147aee1ebba57b86dbbf8a7648456b8d7494936
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793194"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="e00aa-102">ICorDebugMDA — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e00aa-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="e00aa-103">Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="e00aa-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e00aa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e00aa-104">Methods</span></span>  
  
|<span data-ttu-id="e00aa-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e00aa-105">Method</span></span>|<span data-ttu-id="e00aa-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e00aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e00aa-107">GetDescription, metoda</span><span class="sxs-lookup"><span data-stu-id="e00aa-107">GetDescription Method</span></span>](icordebugmda-getdescription-method.md)|<span data-ttu-id="e00aa-108">Pobiera ciąg zawierający opis tego elementu MDA.</span><span class="sxs-lookup"><span data-stu-id="e00aa-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="e00aa-109">GetFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="e00aa-109">GetFlags Method</span></span>](icordebugmda-getflags-method.md)|<span data-ttu-id="e00aa-110">Pobiera flagi skojarzone z tym zdarzeniem MDA.</span><span class="sxs-lookup"><span data-stu-id="e00aa-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="e00aa-111">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="e00aa-111">GetName Method</span></span>](icordebugmda-getname-method.md)|<span data-ttu-id="e00aa-112">Pobiera ciąg zawierający nazwę tego elementu MDA.</span><span class="sxs-lookup"><span data-stu-id="e00aa-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="e00aa-113">GetOSThreadId, metoda</span><span class="sxs-lookup"><span data-stu-id="e00aa-113">GetOSThreadId Method</span></span>](icordebugmda-getosthreadid-method.md)|<span data-ttu-id="e00aa-114">Pobiera identyfikator wątku systemu operacyjnego, na którym jest wykonywane zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="e00aa-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="e00aa-115">GetXML, metoda</span><span class="sxs-lookup"><span data-stu-id="e00aa-115">GetXML Method</span></span>](icordebugmda-getxml-method.md)|<span data-ttu-id="e00aa-116">Pobiera pełny strumień XML skojarzony z tym MDA.</span><span class="sxs-lookup"><span data-stu-id="e00aa-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e00aa-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e00aa-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e00aa-118">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="e00aa-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e00aa-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e00aa-119">Requirements</span></span>  
 <span data-ttu-id="e00aa-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e00aa-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e00aa-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e00aa-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e00aa-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e00aa-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e00aa-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e00aa-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e00aa-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e00aa-124">See also</span></span>

- [<span data-ttu-id="e00aa-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e00aa-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e00aa-126">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="e00aa-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
