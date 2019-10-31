---
title: ICorDebugChain::GetNext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetNext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetNext
helpviewer_keywords:
- GetNext method [.NET Framework debugging]
- ICorDebugChain::GetNext method [.NET Framework debugging]
ms.assetid: 8d9744a5-e08b-4ab2-9855-5c22711cc1e6
topic_type:
- apiref
ms.openlocfilehash: 132734dfb6ba9d70836638ab67564fc215e9bc40
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192126"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="95740-102">ICorDebugChain::GetNext — Metoda</span><span class="sxs-lookup"><span data-stu-id="95740-102">ICorDebugChain::GetNext Method</span></span>
<span data-ttu-id="95740-103">Pobiera następny łańcuch ramek dla wątku.</span><span class="sxs-lookup"><span data-stu-id="95740-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95740-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="95740-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95740-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95740-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="95740-106">określoną Wskaźnik do adresu obiektu ICorDebugChain, który reprezentuje następny łańcuch ramek dla wątku.</span><span class="sxs-lookup"><span data-stu-id="95740-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="95740-107">Jeśli ten łańcuch jest ostatnim łańcuchem, `ppChain` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="95740-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95740-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95740-108">Requirements</span></span>  
 <span data-ttu-id="95740-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95740-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95740-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="95740-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95740-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="95740-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95740-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95740-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
