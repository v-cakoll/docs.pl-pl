---
title: ICorDebugChain::GetStackRange — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac40927ac9469e4a2fb74fb550287130b9bb9f83
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481563"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="3a67f-102">ICorDebugChain::GetStackRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a67f-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="3a67f-103">Pobiera zakres adresów segment stosu dla tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="3a67f-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a67f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a67f-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a67f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a67f-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="3a67f-106">[out] Wskaźnik do `CORDB_ADDRESS` wartość, która jest adres początkowy segment stosu.</span><span class="sxs-lookup"><span data-stu-id="3a67f-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="3a67f-107">[out] Wskaźnik do `CORDB_ADDRESS` wartość, która jest adres końcowy segmentu stosu.</span><span class="sxs-lookup"><span data-stu-id="3a67f-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a67f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a67f-108">Remarks</span></span>  
 <span data-ttu-id="3a67f-109">Zakresu liczbowego ma znaczenie tylko w przypadku porównywania lokalizacje ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="3a67f-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="3a67f-110">Nie można wprowadzać żadnych założeń dotyczących co rzeczywiście jest przechowywana na stosie.</span><span class="sxs-lookup"><span data-stu-id="3a67f-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a67f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a67f-111">Requirements</span></span>  
 <span data-ttu-id="3a67f-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a67f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a67f-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a67f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a67f-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a67f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a67f-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a67f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
