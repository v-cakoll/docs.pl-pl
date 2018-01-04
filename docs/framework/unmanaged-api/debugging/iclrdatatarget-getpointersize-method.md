---
title: "ICLRDataTarget::GetPointerSize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetPointerSize
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ca35246b82ed4adc982b6e7b157398d230dabe4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="e1865-102">ICLRDataTarget::GetPointerSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="e1865-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="e1865-103">Pobiera rozmiar w bajtach, który używa procesu docelowego typu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="e1865-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="e1865-104">Ta metoda jest wywoływana przez usługi dostępu danych środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="e1865-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1865-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1865-105">Syntax</span></span>  
  
```  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1865-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1865-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="e1865-107">[out] Wskaźnik do wartość całkowita określająca rozmiar w bajtach, wskaźnika w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="e1865-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1865-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1865-108">Remarks</span></span>  
 <span data-ttu-id="e1865-109">Ta metoda jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1865-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1865-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1865-110">Requirements</span></span>  
 <span data-ttu-id="e1865-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1865-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1865-112">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e1865-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e1865-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1865-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1865-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1865-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1865-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1865-115">See Also</span></span>  
 [<span data-ttu-id="e1865-116">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1865-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
