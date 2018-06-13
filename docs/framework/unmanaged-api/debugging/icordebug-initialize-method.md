---
title: ICorDebug::Initialize — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa79382d597d303d492e3a441c15a422697be279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405970"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="a63dd-102">ICorDebug::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="a63dd-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="a63dd-103">Inicjuje `ICorDebug` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a63dd-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a63dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a63dd-104">Syntax</span></span>  
  
```  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a63dd-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a63dd-105">Remarks</span></span>  
 <span data-ttu-id="a63dd-106">Debuger musi wywołać `Initialize` podczas tworzenia usługi Czas zainicjować debugowanie.</span><span class="sxs-lookup"><span data-stu-id="a63dd-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="a63dd-107">Ta metoda musi zostać wywołana przed innej metody w `ICorDebug` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="a63dd-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a63dd-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a63dd-108">Requirements</span></span>  
 <span data-ttu-id="a63dd-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a63dd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a63dd-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a63dd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a63dd-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a63dd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a63dd-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a63dd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a63dd-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a63dd-113">See Also</span></span>  
 [<span data-ttu-id="a63dd-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="a63dd-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
