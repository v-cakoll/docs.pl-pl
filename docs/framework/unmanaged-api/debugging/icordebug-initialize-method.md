---
title: "ICorDebug::Initialize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dff8e5472879bfffb0489f113e9d88527569fa1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="49936-102">ICorDebug::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="49936-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="49936-103">Inicjuje `ICorDebug` obiektu.</span><span class="sxs-lookup"><span data-stu-id="49936-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49936-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49936-104">Syntax</span></span>  
  
```  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="49936-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49936-105">Remarks</span></span>  
 <span data-ttu-id="49936-106">Debuger musi wywołać `Initialize` podczas tworzenia usługi Czas zainicjować debugowanie.</span><span class="sxs-lookup"><span data-stu-id="49936-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="49936-107">Ta metoda musi zostać wywołana przed innej metody w `ICorDebug` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="49936-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49936-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49936-108">Requirements</span></span>  
 <span data-ttu-id="49936-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49936-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49936-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49936-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49936-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49936-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49936-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49936-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49936-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49936-113">See Also</span></span>  
 [<span data-ttu-id="49936-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="49936-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
