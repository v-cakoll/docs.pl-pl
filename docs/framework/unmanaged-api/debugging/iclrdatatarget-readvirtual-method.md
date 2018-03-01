---
title: "ICLRDataTarget::ReadVirtual — Metoda"
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
- ICLRDataTarget.ReadVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 84d1a8c37bf9d065317688f42bd554108fd92974
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="18d91-102">ICLRDataTarget::ReadVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="18d91-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="18d91-103">Odczytuje dane z adresów pamięci wirtualnej określony w buforze określona.</span><span class="sxs-lookup"><span data-stu-id="18d91-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18d91-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="18d91-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18d91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18d91-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="18d91-106">[in] CLRDATA_ADDRESS, która przechowuje adresów pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="18d91-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="18d91-107">[out] Wskaźnik do buforu, który odbiera dane.</span><span class="sxs-lookup"><span data-stu-id="18d91-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="18d91-108">[in] Długość buforu.</span><span class="sxs-lookup"><span data-stu-id="18d91-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="18d91-109">[out] Wskaźnik do liczba bajtów zwrócona.</span><span class="sxs-lookup"><span data-stu-id="18d91-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18d91-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="18d91-110">Requirements</span></span>  
 <span data-ttu-id="18d91-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18d91-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18d91-112">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="18d91-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="18d91-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18d91-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18d91-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18d91-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d91-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18d91-115">See Also</span></span>  
 [<span data-ttu-id="18d91-116">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="18d91-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
