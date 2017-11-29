---
title: "ICorDebugILFrame::EnumerateArguments — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.EnumerateArguments
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf345f3fa684b57a33e3452916535b1cd7db3c8b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="bdfa9-102">ICorDebugILFrame::EnumerateArguments — Metoda</span><span class="sxs-lookup"><span data-stu-id="bdfa9-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="bdfa9-103">Pobiera moduł wyliczający dla argumentów do tej ramki.</span><span class="sxs-lookup"><span data-stu-id="bdfa9-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdfa9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bdfa9-104">Syntax</span></span>  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bdfa9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bdfa9-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="bdfa9-106">[out] Wskaźnik do adresu ICorDebugValueEnum obiektu, który moduł wyliczający dla argumentów do tej ramki.</span><span class="sxs-lookup"><span data-stu-id="bdfa9-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdfa9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bdfa9-107">Remarks</span></span>  
 <span data-ttu-id="bdfa9-108">`EnumerateArguments`Pobiera moduł wyliczający, który można wyświetlić listę dostępnych w ramce wywołania reprezentowanego przez ten obiekt ICorDebugILFrame argumentów.</span><span class="sxs-lookup"><span data-stu-id="bdfa9-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="bdfa9-109">Lista zawiera argumenty, które są [vararg](/cpp/windows/vararg) (to znaczy zmienną liczbę argumentów) oraz argumentów, które nie są `vararg`.</span><span class="sxs-lookup"><span data-stu-id="bdfa9-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdfa9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bdfa9-110">Requirements</span></span>  
 <span data-ttu-id="bdfa9-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdfa9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdfa9-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdfa9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdfa9-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdfa9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdfa9-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdfa9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
