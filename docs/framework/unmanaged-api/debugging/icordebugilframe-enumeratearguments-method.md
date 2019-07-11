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
ms.openlocfilehash: 499f58cc0a3f2d1b3c159435ed7d9b523f25e29e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757892"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="3fc3e-102">ICorDebugILFrame::EnumerateArguments — Metoda</span><span class="sxs-lookup"><span data-stu-id="3fc3e-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="3fc3e-103">Pobiera moduł wyliczający dla argumentów w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="3fc3e-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fc3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3fc3e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fc3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fc3e-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="3fc3e-106">[out] Wskaźnik na adres icordebugvalueenum — obiekt, który jest moduł wyliczający dla argumentów w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="3fc3e-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fc3e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3fc3e-107">Remarks</span></span>  
 <span data-ttu-id="3fc3e-108">`EnumerateArguments` Pobiera moduł wyliczający, który można wyświetlić listę dostępnych w ramce wywołań, który jest reprezentowany przez ten obiekt ICorDebugILFrame argumentów.</span><span class="sxs-lookup"><span data-stu-id="3fc3e-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="3fc3e-109">Lista zawiera argumenty, które są [vararg](/cpp/windows/vararg) (czyli zmienną liczbę argumentów) oraz argumenty, które nie są `vararg`.</span><span class="sxs-lookup"><span data-stu-id="3fc3e-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fc3e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3fc3e-110">Requirements</span></span>  
 <span data-ttu-id="3fc3e-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fc3e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fc3e-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fc3e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fc3e-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fc3e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fc3e-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fc3e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
