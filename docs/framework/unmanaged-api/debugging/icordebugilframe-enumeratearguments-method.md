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
ms.openlocfilehash: 3945b1dea62dc0616d669356faf60f0d09cfb084
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210309"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="62196-102">ICorDebugILFrame::EnumerateArguments — Metoda</span><span class="sxs-lookup"><span data-stu-id="62196-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="62196-103">Pobiera moduł wyliczający dla argumentów w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="62196-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62196-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62196-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62196-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62196-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="62196-106">określoną Wskaźnik do adresu obiektu ICorDebugValueEnum, który jest modułem wyliczającym dla argumentów w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="62196-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62196-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62196-107">Remarks</span></span>  
 <span data-ttu-id="62196-108">`EnumerateArguments`Pobiera moduł wyliczający, który może wyświetlać listę argumentów dostępnych w ramce wywołania, która jest reprezentowana przez ten obiekt ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="62196-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="62196-109">Lista będzie zawierać argumenty, które są [vararg](/cpp/windows/vararg) (czyli zmienną liczbę argumentów), a także argumenty, które nie są `vararg` .</span><span class="sxs-lookup"><span data-stu-id="62196-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62196-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62196-110">Requirements</span></span>  
 <span data-ttu-id="62196-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62196-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62196-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="62196-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62196-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="62196-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62196-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62196-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
