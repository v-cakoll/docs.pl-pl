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
ms.openlocfilehash: d9430c5a1f37a0507b383ea5437f7d7fed706c43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123860"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="ce33e-102">ICorDebugChain::GetStackRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="ce33e-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="ce33e-103">Pobiera zakres adresów segmentu stosu dla tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="ce33e-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce33e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce33e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce33e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce33e-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="ce33e-106">określoną Wskaźnik do `CORDB_ADDRESS` wartości, który jest adresem początkowym segmentu stosu.</span><span class="sxs-lookup"><span data-stu-id="ce33e-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="ce33e-107">określoną Wskaźnik do wartości `CORDB_ADDRESS`, która jest adresem końcowym segmentu stosu.</span><span class="sxs-lookup"><span data-stu-id="ce33e-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce33e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce33e-108">Remarks</span></span>  
 <span data-ttu-id="ce33e-109">Zakres liczbowy jest zrozumiały tylko dla porównania lokalizacji ramek stosu.</span><span class="sxs-lookup"><span data-stu-id="ce33e-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="ce33e-110">Nie można wykonać żadnych założeń dotyczących tego, co jest rzeczywiście przechowywane na stosie.</span><span class="sxs-lookup"><span data-stu-id="ce33e-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce33e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce33e-111">Requirements</span></span>  
 <span data-ttu-id="ce33e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce33e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce33e-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ce33e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce33e-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ce33e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce33e-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce33e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
