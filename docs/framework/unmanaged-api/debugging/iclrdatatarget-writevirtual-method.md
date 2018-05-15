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
ms.openlocfilehash: e55bc18c7a41e235d1ba6274067c45c26dc7262a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="511bd-102">ICLRDataTarget::WriteVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="511bd-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="511bd-103">Zapisuje dane z określonego bufora na adres określony pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="511bd-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="511bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="511bd-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="511bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="511bd-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="511bd-106">[in] CLRDATA_ADDRESS, która przechowuje adresów pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="511bd-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="511bd-107">[in] Wskaźnik do buforu, który przechowuje dane do zapisania.</span><span class="sxs-lookup"><span data-stu-id="511bd-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="511bd-108">[in] Liczba bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="511bd-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="511bd-109">[out] Wskaźnik do rzeczywistą liczbę bajtów, które zostały zapisane.</span><span class="sxs-lookup"><span data-stu-id="511bd-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="511bd-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="511bd-110">Requirements</span></span>  
 <span data-ttu-id="511bd-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="511bd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="511bd-112">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="511bd-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="511bd-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="511bd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="511bd-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="511bd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="511bd-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="511bd-115">See Also</span></span>  
 [<span data-ttu-id="511bd-116">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="511bd-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
