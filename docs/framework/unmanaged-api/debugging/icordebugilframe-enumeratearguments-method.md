---
title: "ICorDebugILFrame::EnumerateArguments — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 474118abc505928d16737d792a619e75f1209344
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="b0a44-102">ICorDebugILFrame::EnumerateArguments — Metoda</span><span class="sxs-lookup"><span data-stu-id="b0a44-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="b0a44-103">Pobiera moduł wyliczający dla argumentów do tej ramki.</span><span class="sxs-lookup"><span data-stu-id="b0a44-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0a44-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0a44-104">Syntax</span></span>  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0a44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0a44-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="b0a44-106">[out] Wskaźnik do adresu ICorDebugValueEnum obiektu, który moduł wyliczający dla argumentów do tej ramki.</span><span class="sxs-lookup"><span data-stu-id="b0a44-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0a44-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0a44-107">Remarks</span></span>  
 <span data-ttu-id="b0a44-108">`EnumerateArguments`Pobiera moduł wyliczający, który można wyświetlić listę dostępnych w ramce wywołania reprezentowanego przez ten obiekt ICorDebugILFrame argumentów.</span><span class="sxs-lookup"><span data-stu-id="b0a44-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="b0a44-109">Lista zawiera argumenty, które są [vararg](/cpp/windows/vararg) (to znaczy zmienną liczbę argumentów) oraz argumentów, które nie są `vararg`.</span><span class="sxs-lookup"><span data-stu-id="b0a44-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0a44-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0a44-110">Requirements</span></span>  
 <span data-ttu-id="b0a44-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0a44-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0a44-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0a44-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0a44-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0a44-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0a44-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0a44-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
