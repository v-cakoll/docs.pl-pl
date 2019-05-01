---
title: ICorDebugILFrame::EnumerateArguments — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49d7fb1de0b2ea63c1a766023b23acc42e027af8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995569"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="ebf33-102">ICorDebugILFrame::EnumerateArguments — Metoda</span><span class="sxs-lookup"><span data-stu-id="ebf33-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="ebf33-103">Pobiera moduł wyliczający dla argumentów w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="ebf33-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf33-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebf33-104">Syntax</span></span>  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebf33-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebf33-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="ebf33-106">[out] Wskaźnik na adres icordebugvalueenum — obiekt, który jest moduł wyliczający dla argumentów w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="ebf33-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebf33-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ebf33-107">Remarks</span></span>  
 <span data-ttu-id="ebf33-108">`EnumerateArguments` Pobiera moduł wyliczający, który można wyświetlić listę dostępnych w ramce wywołań, który jest reprezentowany przez ten obiekt ICorDebugILFrame argumentów.</span><span class="sxs-lookup"><span data-stu-id="ebf33-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="ebf33-109">Lista zawiera argumenty, które są [vararg](/cpp/windows/vararg) (czyli zmienną liczbę argumentów) oraz argumenty, które nie są `vararg`.</span><span class="sxs-lookup"><span data-stu-id="ebf33-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebf33-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebf33-110">Requirements</span></span>  
 <span data-ttu-id="ebf33-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebf33-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebf33-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebf33-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebf33-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebf33-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebf33-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebf33-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
