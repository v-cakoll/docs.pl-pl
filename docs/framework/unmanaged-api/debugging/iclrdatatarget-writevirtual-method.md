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
ms.openlocfilehash: bd2f67c2d7230d3873b4dc0df73ac1be778a0828
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179095"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="29a13-102">ICLRDataTarget::WriteVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="29a13-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="29a13-103">Zapisuje dane z określonego buforu na określony adres pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="29a13-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29a13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29a13-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29a13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29a13-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="29a13-106">[w] CLRDATA_ADDRESS, który przechowuje adres pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="29a13-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="29a13-107">[w] Wskaźnik do buforu, który przechowuje dane do zapisania.</span><span class="sxs-lookup"><span data-stu-id="29a13-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="29a13-108">[w] Liczba bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="29a13-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="29a13-109">[na zewnątrz] Wskaźnik do rzeczywistej liczby bajtów, które zostały zapisane.</span><span class="sxs-lookup"><span data-stu-id="29a13-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29a13-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29a13-110">Requirements</span></span>  
 <span data-ttu-id="29a13-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29a13-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29a13-112">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="29a13-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="29a13-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29a13-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29a13-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29a13-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29a13-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29a13-115">See also</span></span>

- [<span data-ttu-id="29a13-116">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="29a13-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
