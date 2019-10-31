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
ms.openlocfilehash: d74c5a6f966201c8ca9d2854de2e9986e7f1d0fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131031"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="39740-102">ICorDebugILFrame::EnumerateArguments — Metoda</span><span class="sxs-lookup"><span data-stu-id="39740-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="39740-103">Pobiera moduł wyliczający dla argumentów w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="39740-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39740-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="39740-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39740-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="39740-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="39740-106">określoną Wskaźnik do adresu obiektu ICorDebugValueEnum, który jest modułem wyliczającym dla argumentów w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="39740-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39740-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39740-107">Remarks</span></span>  
 <span data-ttu-id="39740-108">`EnumerateArguments` Pobiera moduł wyliczający, który może wyświetlać listę argumentów dostępnych w ramce wywołania, która jest reprezentowana przez ten obiekt ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="39740-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="39740-109">Lista będzie zawierać argumenty, które są [vararg](/cpp/windows/vararg) (czyli zmienną liczbę argumentów), a także argumenty, które nie są `vararg`.</span><span class="sxs-lookup"><span data-stu-id="39740-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39740-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39740-110">Requirements</span></span>  
 <span data-ttu-id="39740-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39740-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39740-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="39740-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39740-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="39740-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39740-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39740-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
