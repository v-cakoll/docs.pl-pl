---
title: ICorDebugILFrame::EnumerateLocalVariables — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cc9601105d05740e6db0a41bae521bd9a276d74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988653"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="488df-102">ICorDebugILFrame::EnumerateLocalVariables — Metoda</span><span class="sxs-lookup"><span data-stu-id="488df-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="488df-103">Pobiera moduł wyliczający dla zmiennych lokalnych w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="488df-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="488df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="488df-104">Syntax</span></span>  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="488df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="488df-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="488df-106">[out] Wskaźnik na adres icordebugvalueenum — obiekt, który jest moduł wyliczający dla zmiennych lokalnych w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="488df-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="488df-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="488df-107">Remarks</span></span>  
 <span data-ttu-id="488df-108">`EnumerateLocalVariables` Pobiera moduł wyliczający, który można wyświetlić listę zmiennych lokalnych dostępnych w ramce wywołań, który jest reprezentowany przez ten obiekt ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="488df-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="488df-109">Listy mogą nie uwzględniać całego zmiennych lokalnych w uruchomionej funkcji, ponieważ niektóre z nich nie może być aktywne.</span><span class="sxs-lookup"><span data-stu-id="488df-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="488df-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="488df-110">Requirements</span></span>  
 <span data-ttu-id="488df-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="488df-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="488df-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="488df-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="488df-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="488df-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="488df-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="488df-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
