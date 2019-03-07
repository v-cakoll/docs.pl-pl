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
ms.openlocfilehash: a1d9fdef9d183a03fd7f335a13683e1d1a3f95c8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485723"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="17bce-102">ICLRDataTarget::WriteVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="17bce-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="17bce-103">Zapisuje dane z określonego bufora do adresu określonego pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="17bce-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17bce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="17bce-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17bce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17bce-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="17bce-106">[in] CLRDATA_ADDRESS, która przechowuje adres pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="17bce-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="17bce-107">[in] Wskaźnik do buforu, który przechowuje dane do zapisania.</span><span class="sxs-lookup"><span data-stu-id="17bce-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="17bce-108">[in] Liczba bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="17bce-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="17bce-109">[out] Wskaźnik do rzeczywistej liczby bajtów, które zostały napisane.</span><span class="sxs-lookup"><span data-stu-id="17bce-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17bce-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="17bce-110">Requirements</span></span>  
 <span data-ttu-id="17bce-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17bce-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17bce-112">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="17bce-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="17bce-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17bce-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17bce-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17bce-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17bce-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17bce-115">See also</span></span>
- [<span data-ttu-id="17bce-116">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="17bce-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
