---
title: ICLRDataTarget::ReadVirtual — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38e2ec063d46ce9c890927391107888032e31378
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092598"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="552e7-102">ICLRDataTarget::ReadVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="552e7-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="552e7-103">Odczytuje dane z adresu określonego pamięci wirtualnej do określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="552e7-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="552e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="552e7-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="552e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="552e7-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="552e7-106">[in] CLRDATA_ADDRESS, która przechowuje adres pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="552e7-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="552e7-107">[out] Wskaźnik do buforu, który odbiera dane.</span><span class="sxs-lookup"><span data-stu-id="552e7-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="552e7-108">[in] Długość buforu.</span><span class="sxs-lookup"><span data-stu-id="552e7-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="552e7-109">[out] Wskaźnik do liczby bajtów zwróconych.</span><span class="sxs-lookup"><span data-stu-id="552e7-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="552e7-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="552e7-110">Requirements</span></span>  
 <span data-ttu-id="552e7-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="552e7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="552e7-112">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="552e7-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="552e7-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="552e7-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="552e7-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="552e7-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="552e7-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="552e7-115">See also</span></span>

- [<span data-ttu-id="552e7-116">ICLRDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="552e7-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
