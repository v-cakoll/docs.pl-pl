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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6020950a7ee742f09af67fe856692e19c066e288
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658051"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="50741-102">ICorDebug::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="50741-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="50741-103">Pobiera wskaźnik do wystąpienia "ICorDebugProcess" dla określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="50741-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50741-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50741-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50741-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50741-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="50741-106">[in] Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="50741-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="50741-107">[out] Wskaźnik na adres `ICorDebugProcess` wystąpienia dla określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="50741-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50741-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50741-108">Requirements</span></span>  
 <span data-ttu-id="50741-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50741-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50741-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50741-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50741-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50741-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50741-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50741-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50741-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50741-113">See also</span></span>
- [<span data-ttu-id="50741-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="50741-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
