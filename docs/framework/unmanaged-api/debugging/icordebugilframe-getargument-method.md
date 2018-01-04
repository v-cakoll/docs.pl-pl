---
title: "ICorDebugILFrame::GetArgument — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.GetArgument
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6b1c097d830af4e68035f79670983002c15c16d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="44cb3-102">ICorDebugILFrame::GetArgument — Metoda</span><span class="sxs-lookup"><span data-stu-id="44cb3-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="44cb3-103">Pobiera wartość określonego argumentu w tej ramce stosu język pośredni (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="44cb3-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44cb3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44cb3-104">Syntax</span></span>  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44cb3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44cb3-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="44cb3-106">[in] Indeks argumentu w tej ramki stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="44cb3-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="44cb3-107">[out] Wskaźnik do adresu ICorDebugValue obiekt, który reprezentuje pobrana wartość.</span><span class="sxs-lookup"><span data-stu-id="44cb3-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44cb3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44cb3-108">Remarks</span></span>  
 <span data-ttu-id="44cb3-109">`GetArgument` Metody można użyć w ramce stosu MSIL lub w ramce skompilowanych just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="44cb3-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44cb3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44cb3-110">Requirements</span></span>  
 <span data-ttu-id="44cb3-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44cb3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44cb3-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44cb3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44cb3-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44cb3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44cb3-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44cb3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
