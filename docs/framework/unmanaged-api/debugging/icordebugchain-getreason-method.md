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
ms.openlocfilehash: e51ee2e4d44af547c82a21a782121976d07118c5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124719"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="314ca-102">ICorDebugChain::GetReason — Metoda</span><span class="sxs-lookup"><span data-stu-id="314ca-102">ICorDebugChain::GetReason Method</span></span>
<span data-ttu-id="314ca-103">Pobiera przyczynę Genesis tego łańcucha wywołującego.</span><span class="sxs-lookup"><span data-stu-id="314ca-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="314ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="314ca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="314ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="314ca-105">Parameters</span></span>  
 `pReason`  
 <span data-ttu-id="314ca-106">określoną Wskaźnik do wartości (kombinacja bitowa) wyliczenia CorDebugChainReason —, która wskazuje przyczynę Genesis tego łańcucha wywołującego.</span><span class="sxs-lookup"><span data-stu-id="314ca-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="314ca-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="314ca-107">Requirements</span></span>  
 <span data-ttu-id="314ca-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="314ca-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="314ca-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="314ca-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="314ca-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="314ca-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="314ca-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="314ca-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
