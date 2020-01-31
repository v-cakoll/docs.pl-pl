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
ms.openlocfilehash: 3d27cf1987d7e9896885f87857554f4039c8d714
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788981"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="f5af8-102">ICorDebug::Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="f5af8-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="f5af8-103">Inicjuje obiekt `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="f5af8-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5af8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5af8-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f5af8-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5af8-105">Remarks</span></span>  
 <span data-ttu-id="f5af8-106">Debuger musi wywołać `Initialize` w czasie tworzenia, aby zainicjować usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="f5af8-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="f5af8-107">Ta metoda musi być wywoływana przed wywołaniem innej metody na `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="f5af8-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5af8-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5af8-108">Requirements</span></span>  
 <span data-ttu-id="f5af8-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5af8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5af8-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5af8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5af8-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f5af8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5af8-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5af8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5af8-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5af8-113">See also</span></span>

- [<span data-ttu-id="f5af8-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5af8-114">ICorDebug Interface</span></span>](icordebug-interface.md)
