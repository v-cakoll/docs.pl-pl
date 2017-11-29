---
title: "IcorDebugVariableHome::GetLiveRange — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetLiveRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8554bf2667f3542b3164b60eaed998087fe175d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="318ce-102">IcorDebugVariableHome::GetLiveRange — metoda</span><span class="sxs-lookup"><span data-stu-id="318ce-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="318ce-103">Pobiera natywnego zakresu, w którym ta zmienna jest na żywo.</span><span class="sxs-lookup"><span data-stu-id="318ce-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="318ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="318ce-104">Syntax</span></span>  
  
```  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="318ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="318ce-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="318ce-106">[out] Przesunięcie logiczne, jaką zmienna jest pierwszy na żywo.</span><span class="sxs-lookup"><span data-stu-id="318ce-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="318ce-107">[out] Przesunięcie logiczne natychmiast po punkt, w którym zmienna jest ostatni na żywo.</span><span class="sxs-lookup"><span data-stu-id="318ce-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="318ce-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="318ce-108">Requirements</span></span>  
 <span data-ttu-id="318ce-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="318ce-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="318ce-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="318ce-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="318ce-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="318ce-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="318ce-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="318ce-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="318ce-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="318ce-113">See Also</span></span>  
 [<span data-ttu-id="318ce-114">Interfejs ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="318ce-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
