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
ms.openlocfilehash: 0c26a2df3f73af5ebd1f8b735d7662bb23ba4228
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134168"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="e767f-102">ICLRDataTarget::ReadVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="e767f-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="e767f-103">Odczytuje dane z określonego adresu pamięci wirtualnej do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="e767f-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e767f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e767f-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e767f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e767f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="e767f-106">podczas CLRDATA_ADDRESS, który przechowuje adres pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="e767f-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e767f-107">określoną Wskaźnik do buforu, który odbiera dane.</span><span class="sxs-lookup"><span data-stu-id="e767f-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="e767f-108">podczas Długość buforu.</span><span class="sxs-lookup"><span data-stu-id="e767f-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="e767f-109">określoną Wskaźnik do liczby zwracanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="e767f-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e767f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e767f-110">Requirements</span></span>  
 <span data-ttu-id="e767f-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e767f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e767f-112">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="e767f-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e767f-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e767f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e767f-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e767f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e767f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e767f-115">See also</span></span>

- [<span data-ttu-id="e767f-116">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="e767f-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
