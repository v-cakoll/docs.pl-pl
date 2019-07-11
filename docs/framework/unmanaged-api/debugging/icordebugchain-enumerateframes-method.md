---
title: ICorDebugChain::EnumerateFrames — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc647805fcb7d8354a2540ac9424dc7155853444
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745035"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="cae13-102">ICorDebugChain::EnumerateFrames — Metoda</span><span class="sxs-lookup"><span data-stu-id="cae13-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="cae13-103">Pobiera moduł wyliczający, który zawiera wszystkie ramki stosu zarządzanych w łańcuchu, począwszy od najbardziej aktualną ramki.</span><span class="sxs-lookup"><span data-stu-id="cae13-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cae13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cae13-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cae13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cae13-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="cae13-106">[out] Wskaźnik na adres icordebugframeenum — obiekt, który jest moduł wyliczający ramek stosu.</span><span class="sxs-lookup"><span data-stu-id="cae13-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cae13-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cae13-107">Remarks</span></span>  
 <span data-ttu-id="cae13-108">Łańcuch reprezentuje stosu wywołań fizycznych dla wątku.</span><span class="sxs-lookup"><span data-stu-id="cae13-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="cae13-109">`EnumerateFrames` Metodę należy wywoływać tylko w przypadku zarządzanych łańcuchów.</span><span class="sxs-lookup"><span data-stu-id="cae13-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="cae13-110">Interfejsu API debugowania nie udostępnia metody uzyskania ramek, znajdujących się w łańcuchy niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="cae13-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="cae13-111">Debuger, należy użyć inny sposób, aby uzyskać te informacje.</span><span class="sxs-lookup"><span data-stu-id="cae13-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cae13-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cae13-112">Requirements</span></span>  
 <span data-ttu-id="cae13-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cae13-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cae13-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cae13-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cae13-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cae13-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cae13-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cae13-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
