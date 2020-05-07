---
title: ICorDebug::Terminate — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
ms.openlocfilehash: 44bb98f54debb129f951cc388fea81ca0f17b20c
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895320"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="47772-102">ICorDebug::Terminate — Metoda</span><span class="sxs-lookup"><span data-stu-id="47772-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="47772-103">Kończy `ICorDebug` obiekt.</span><span class="sxs-lookup"><span data-stu-id="47772-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47772-104">`Terminate`nie należy wywoływać do momentu odebrania wywołania zwrotnego [ICorDebugManagedCallback:: ExitProcess —](icordebugmanagedcallback-exitprocess-method.md) dla wszystkich debugowanych procesów.</span><span class="sxs-lookup"><span data-stu-id="47772-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47772-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="47772-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="47772-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47772-106">Remarks</span></span>  
 <span data-ttu-id="47772-107">`Terminate`musi być wywoływana, `ICorDebug` gdy obiekt nie jest już wymagany.</span><span class="sxs-lookup"><span data-stu-id="47772-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47772-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47772-108">Requirements</span></span>  
 <span data-ttu-id="47772-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47772-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47772-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="47772-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47772-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="47772-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47772-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47772-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47772-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47772-113">See also</span></span>

- [<span data-ttu-id="47772-114">ICorDebug — Interfejs</span><span class="sxs-lookup"><span data-stu-id="47772-114">ICorDebug Interface</span></span>](icordebug-interface.md)
