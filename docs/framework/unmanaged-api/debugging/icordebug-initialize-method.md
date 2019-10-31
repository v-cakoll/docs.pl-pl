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
ms.openlocfilehash: a5cda98cac0bc3fc6fb101fd0404b062224cb578
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134080"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="6ff72-102">ICorDebug::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="6ff72-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="6ff72-103">Inicjuje obiekt `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="6ff72-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ff72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ff72-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6ff72-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ff72-105">Remarks</span></span>  
 <span data-ttu-id="6ff72-106">Debuger musi wywołać `Initialize` w czasie tworzenia, aby zainicjować usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="6ff72-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="6ff72-107">Ta metoda musi być wywoływana przed wywołaniem innej metody na `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="6ff72-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ff72-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ff72-108">Requirements</span></span>  
 <span data-ttu-id="6ff72-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ff72-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ff72-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6ff72-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ff72-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6ff72-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ff72-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ff72-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ff72-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ff72-113">See also</span></span>

- [<span data-ttu-id="6ff72-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ff72-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
