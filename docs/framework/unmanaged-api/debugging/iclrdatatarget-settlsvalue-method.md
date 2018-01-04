---
title: "ICLRDataTarget::SetTLSValue — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.SetTLSValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d63f20c3a5c90fab2347ea56a8adedc6b8dc5e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="611a6-102">ICLRDataTarget::SetTLSValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="611a6-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="611a6-103">Ustawia wartość w lokalny magazyn wątków (TLS) z określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="611a6-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="611a6-104">Ta metoda jest wywoływana przez wspólne usługi dostępu do danych języka środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="611a6-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="611a6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="611a6-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="611a6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="611a6-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="611a6-107">[in] System operacyjny identyfikator wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="611a6-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="611a6-108">[in] Indeks lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="611a6-108">[in] The index of the location.</span></span> <span data-ttu-id="611a6-109">Ta wartość musi być prawidłowym indeksem w lokalnym magazynie określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="611a6-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="611a6-110">[in] A `CLRDATA_ADDRESS` wartość, która określa wartość do umieszczenia w danej lokalizacji TLS.</span><span class="sxs-lookup"><span data-stu-id="611a6-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="611a6-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="611a6-111">Remarks</span></span>  
 <span data-ttu-id="611a6-112">Ta metoda jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="611a6-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="611a6-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="611a6-113">Requirements</span></span>  
 <span data-ttu-id="611a6-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="611a6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="611a6-115">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="611a6-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="611a6-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="611a6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="611a6-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="611a6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="611a6-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="611a6-118">See Also</span></span>  
 [<span data-ttu-id="611a6-119">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="611a6-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
