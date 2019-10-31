---
title: ICorDebug::GetProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
ms.openlocfilehash: 64ed875059730e91e28ff0903ab93fb25c68910b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134110"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="a60b6-102">ICorDebug::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="a60b6-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="a60b6-103">Pobiera wskaźnik do wystąpienia "ICorDebugProcess" dla określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="a60b6-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a60b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a60b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a60b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a60b6-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="a60b6-106">podczas Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="a60b6-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="a60b6-107">określoną Wskaźnik do adresu `ICorDebugProcess` wystąpienia określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="a60b6-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a60b6-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a60b6-108">Requirements</span></span>  
 <span data-ttu-id="a60b6-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a60b6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a60b6-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a60b6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a60b6-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a60b6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a60b6-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a60b6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a60b6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a60b6-113">See also</span></span>

- [<span data-ttu-id="a60b6-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="a60b6-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
