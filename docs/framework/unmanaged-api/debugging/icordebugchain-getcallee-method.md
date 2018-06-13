---
title: ICorDebugChain::GetCallee — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f050a3d9d37e43713c40896fb162bcf9932c6512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403373"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="9f7e5-102">ICorDebugChain::GetCallee — Metoda</span><span class="sxs-lookup"><span data-stu-id="9f7e5-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="9f7e5-103">Pobiera łańcucha, która została wywołana przez ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="9f7e5-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f7e5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f7e5-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f7e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f7e5-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="9f7e5-106">[out] Wskaźnik do adresu ICorDebugChain obiektu, który odpowiada nazwie łańcucha.</span><span class="sxs-lookup"><span data-stu-id="9f7e5-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="9f7e5-107">Jeśli ten łańcuch jest aktualnie wykonywany (oznacza to, czy ten łańcuch nie oczekuje na nazwie łańcucha do zwrócenia), `ppChain` będzie mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="9f7e5-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f7e5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9f7e5-108">Remarks</span></span>  
 <span data-ttu-id="9f7e5-109">Ten łańcuch będzie oczekiwał na nazwie łańcucha do zwrócenia przed kontynuuje wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="9f7e5-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="9f7e5-110">Łańcuch o nazwie może być inny wątek w przypadku międzyprocesowe między wątkami.</span><span class="sxs-lookup"><span data-stu-id="9f7e5-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f7e5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9f7e5-111">Requirements</span></span>  
 <span data-ttu-id="9f7e5-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f7e5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f7e5-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f7e5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f7e5-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f7e5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f7e5-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f7e5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
