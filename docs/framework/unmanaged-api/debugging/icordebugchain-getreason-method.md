---
title: ICorDebugChain::GetReason — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
ms.openlocfilehash: 94672c88864efc431acde8f29e406f4fbbc644ee
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894545"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="0542f-102">ICorDebugChain::GetReason — Metoda</span><span class="sxs-lookup"><span data-stu-id="0542f-102">ICorDebugChain::GetReason Method</span></span>
<span data-ttu-id="0542f-103">Pobiera przyczynę Genesis tego łańcucha wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0542f-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0542f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0542f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0542f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0542f-105">Parameters</span></span>  
 `pReason`  
 <span data-ttu-id="0542f-106">określoną Wskaźnik do wartości (kombinacja bitowa) wyliczenia CorDebugChainReason —, która wskazuje przyczynę Genesis tego łańcucha wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0542f-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0542f-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0542f-107">Requirements</span></span>  
 <span data-ttu-id="0542f-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0542f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0542f-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0542f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0542f-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0542f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0542f-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0542f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
