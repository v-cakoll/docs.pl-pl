---
title: "ICorDebugChain::EnumerateFrames — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.EnumerateFrames
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d9df99c239568948c04f61ca4ec5e2b9207930f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="fa7de-102">ICorDebugChain::EnumerateFrames — Metoda</span><span class="sxs-lookup"><span data-stu-id="fa7de-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="fa7de-103">Pobiera moduł wyliczający, który zawiera wszystkie ramki stosu zarządzanych w łańcuchu, zaczynając od ostatniego ramki.</span><span class="sxs-lookup"><span data-stu-id="fa7de-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa7de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa7de-104">Syntax</span></span>  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa7de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa7de-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="fa7de-106">[out] Wskaźnik do adresu ICorDebugFrameEnum obiektu, który moduł wyliczający dla ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="fa7de-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa7de-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa7de-107">Remarks</span></span>  
 <span data-ttu-id="fa7de-108">Łańcuch reprezentuje stosu wywołań fizycznych wątku.</span><span class="sxs-lookup"><span data-stu-id="fa7de-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="fa7de-109">`EnumerateFrames` Metoda powinna być wywoływana tylko do łańcuchów zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="fa7de-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="fa7de-110">Interfejsu API debugowania nie udostępnia metody uzyskania ramki zawarte w łańcuchy niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="fa7de-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="fa7de-111">Aby uzyskać te informacje debugera należy użyć inny sposób.</span><span class="sxs-lookup"><span data-stu-id="fa7de-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa7de-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fa7de-112">Requirements</span></span>  
 <span data-ttu-id="fa7de-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa7de-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa7de-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa7de-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa7de-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa7de-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa7de-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa7de-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
