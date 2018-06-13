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
ms.openlocfilehash: 226f8c431b90d53366aa5e504101e7de581ec570
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402473"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="8212e-102">ICorDebugChain::GetStackRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="8212e-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="8212e-103">Pobiera zakres adresów segmentu stosu dla tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="8212e-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8212e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8212e-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8212e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8212e-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="8212e-106">[out] Wskaźnik do `CORDB_ADDRESS` wartość, która jest adres początkowy segment stosu.</span><span class="sxs-lookup"><span data-stu-id="8212e-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="8212e-107">[out] Wskaźnik do `CORDB_ADDRESS` wartość, która jest adres końcowy segmentu stosu.</span><span class="sxs-lookup"><span data-stu-id="8212e-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8212e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8212e-108">Remarks</span></span>  
 <span data-ttu-id="8212e-109">Zakres liczb jest znaczący tylko w przypadku porównywania lokalizacje ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="8212e-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="8212e-110">Nie można wprowadzić żadnych założenia dotyczące co to są przechowywane na stosie.</span><span class="sxs-lookup"><span data-stu-id="8212e-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8212e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8212e-111">Requirements</span></span>  
 <span data-ttu-id="8212e-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8212e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8212e-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8212e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8212e-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8212e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8212e-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8212e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
