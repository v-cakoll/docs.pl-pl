---
title: "ICorDebugMDA — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA
helpviewer_keywords: ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 00a003ee060de59fe0eb8ce8f740a620d77a7c85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="24701-102">ICorDebugMDA — Interfejs</span><span class="sxs-lookup"><span data-stu-id="24701-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="24701-103">Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="24701-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="24701-104">Metody</span><span class="sxs-lookup"><span data-stu-id="24701-104">Methods</span></span>  
  
|<span data-ttu-id="24701-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="24701-105">Method</span></span>|<span data-ttu-id="24701-106">Opis</span><span class="sxs-lookup"><span data-stu-id="24701-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="24701-107">GetDescription — metoda</span><span class="sxs-lookup"><span data-stu-id="24701-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="24701-108">Pobiera ciąg zawierający opis to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="24701-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="24701-109">GetFlags — metoda</span><span class="sxs-lookup"><span data-stu-id="24701-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="24701-110">Pobiera flagi skojarzone z tym MDA.</span><span class="sxs-lookup"><span data-stu-id="24701-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="24701-111">GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="24701-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="24701-112">Pobiera ciąg zawierający nazwę to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="24701-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="24701-113">GetOSThreadId — metoda</span><span class="sxs-lookup"><span data-stu-id="24701-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="24701-114">Pobiera identyfikator wątku systemu operacyjnego, na którym jest wykonywane to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="24701-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="24701-115">GetXML — metoda</span><span class="sxs-lookup"><span data-stu-id="24701-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="24701-116">Pobiera pełną strumień XML skojarzony z tym MDA.</span><span class="sxs-lookup"><span data-stu-id="24701-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24701-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24701-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24701-118">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="24701-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24701-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24701-119">Requirements</span></span>  
 <span data-ttu-id="24701-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24701-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24701-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24701-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24701-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24701-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24701-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24701-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24701-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24701-124">See Also</span></span>  
 [<span data-ttu-id="24701-125">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="24701-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="24701-126">Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="24701-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
