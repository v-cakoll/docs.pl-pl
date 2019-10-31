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
ms.openlocfilehash: c6b4303163140c9c5553d02855c64dd2a3f5b134
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112738"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="40c68-102">ICLRDataTarget::WriteVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="40c68-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="40c68-103">Zapisuje dane z określonego buforu na określonym adresie pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="40c68-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c68-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40c68-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40c68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40c68-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="40c68-106">podczas CLRDATA_ADDRESS, który przechowuje adres pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="40c68-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="40c68-107">podczas Wskaźnik do buforu, który przechowuje dane do zapisania.</span><span class="sxs-lookup"><span data-stu-id="40c68-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="40c68-108">podczas Liczba bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="40c68-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="40c68-109">określoną Wskaźnik do rzeczywistej liczby zapisanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="40c68-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40c68-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40c68-110">Requirements</span></span>  
 <span data-ttu-id="40c68-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40c68-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40c68-112">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="40c68-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="40c68-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="40c68-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40c68-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40c68-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c68-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40c68-115">See also</span></span>

- [<span data-ttu-id="40c68-116">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="40c68-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
