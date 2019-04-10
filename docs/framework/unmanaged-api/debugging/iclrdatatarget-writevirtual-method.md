---
title: ICLRDataTarget::WriteVirtual — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a0beb9a0b1ef2db6ff32fee1b55b3478794509a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219736"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="226de-102">ICLRDataTarget::WriteVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="226de-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="226de-103">Zapisuje dane z określonego bufora do adresu określonego pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="226de-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="226de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="226de-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="226de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="226de-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="226de-106">[in] CLRDATA_ADDRESS, która przechowuje adres pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="226de-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="226de-107">[in] Wskaźnik do buforu, który przechowuje dane do zapisania.</span><span class="sxs-lookup"><span data-stu-id="226de-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="226de-108">[in] Liczba bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="226de-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="226de-109">[out] Wskaźnik do rzeczywistej liczby bajtów, które zostały napisane.</span><span class="sxs-lookup"><span data-stu-id="226de-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="226de-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="226de-110">Requirements</span></span>  
 <span data-ttu-id="226de-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="226de-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="226de-112">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="226de-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="226de-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="226de-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="226de-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="226de-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="226de-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="226de-115">See also</span></span>

- [<span data-ttu-id="226de-116">ICLRDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="226de-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
