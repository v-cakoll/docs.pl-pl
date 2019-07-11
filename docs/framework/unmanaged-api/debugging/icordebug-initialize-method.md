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
ms.openlocfilehash: 80465c8d1f1f9e09c0675de1667b999b332b9f6b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738148"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="caf83-102">ICorDebug::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="caf83-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="caf83-103">Inicjuje `ICorDebug` obiektu.</span><span class="sxs-lookup"><span data-stu-id="caf83-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caf83-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="caf83-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="caf83-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="caf83-105">Remarks</span></span>  
 <span data-ttu-id="caf83-106">Debuger musi wywołać `Initialize` podczas tworzenia usługi czasu można zainicjować debugowania.</span><span class="sxs-lookup"><span data-stu-id="caf83-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="caf83-107">Ta metoda musi zostać wywołana przed każda inna metoda na `ICorDebug` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="caf83-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caf83-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="caf83-108">Requirements</span></span>  
 <span data-ttu-id="caf83-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caf83-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caf83-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="caf83-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="caf83-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="caf83-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="caf83-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caf83-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caf83-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="caf83-113">See also</span></span>

- [<span data-ttu-id="caf83-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="caf83-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
