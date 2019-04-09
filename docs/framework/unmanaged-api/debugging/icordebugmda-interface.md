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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cea8f6827d3e361b3f6498e6612d8b11a2357285
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098672"
---
# <a name="icordebugmda-interface"></a><span data-ttu-id="29959-102">ICorDebugMDA — Interfejs</span><span class="sxs-lookup"><span data-stu-id="29959-102">ICorDebugMDA Interface</span></span>
<span data-ttu-id="29959-103">Reprezentuje komunikat asystenta zarządzanego debugowania (MDA).</span><span class="sxs-lookup"><span data-stu-id="29959-103">Represents a managed debugging assistant (MDA) message.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29959-104">Metody</span><span class="sxs-lookup"><span data-stu-id="29959-104">Methods</span></span>  
  
|<span data-ttu-id="29959-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="29959-105">Method</span></span>|<span data-ttu-id="29959-106">Opis</span><span class="sxs-lookup"><span data-stu-id="29959-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29959-107">GetDescription, metoda</span><span class="sxs-lookup"><span data-stu-id="29959-107">GetDescription Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|<span data-ttu-id="29959-108">Pobiera ciąg zawierający opis to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="29959-108">Gets a string containing a description of this MDA.</span></span>|  
|[<span data-ttu-id="29959-109">GetFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="29959-109">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|<span data-ttu-id="29959-110">Pobiera flagi skojarzone z tego MDA.</span><span class="sxs-lookup"><span data-stu-id="29959-110">Gets the flags associated with this MDA.</span></span>|  
|[<span data-ttu-id="29959-111">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="29959-111">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|<span data-ttu-id="29959-112">Pobiera ciąg zawierający nazwę to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="29959-112">Gets a string containing the name of this MDA.</span></span>|  
|[<span data-ttu-id="29959-113">GetOSThreadId, metoda</span><span class="sxs-lookup"><span data-stu-id="29959-113">GetOSThreadId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|<span data-ttu-id="29959-114">Pobiera identyfikator wątku systemu operacyjnego, na którym jest wykonywane to zdarzenie MDA.</span><span class="sxs-lookup"><span data-stu-id="29959-114">Gets the operating system thread identifier upon which this MDA is executing.</span></span>|  
|[<span data-ttu-id="29959-115">GetXML, metoda</span><span class="sxs-lookup"><span data-stu-id="29959-115">GetXML Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|<span data-ttu-id="29959-116">Pobiera pełną strumień XML skojarzony z tego MDA.</span><span class="sxs-lookup"><span data-stu-id="29959-116">Gets the full XML stream associated with this MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29959-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29959-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29959-118">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="29959-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29959-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29959-119">Requirements</span></span>  
 <span data-ttu-id="29959-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29959-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29959-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29959-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29959-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29959-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="29959-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="29959-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="29959-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29959-124">See also</span></span>

- [<span data-ttu-id="29959-125">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="29959-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="29959-126">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="29959-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
