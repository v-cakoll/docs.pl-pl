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
ms.openlocfilehash: e285df37d83ff73fe29fe293380a4053cb5a9eea
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860556"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="69efe-102">ICLRDataTarget::ReadVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="69efe-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="69efe-103">Odczytuje dane z określonego adresu pamięci wirtualnej do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="69efe-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69efe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69efe-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69efe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69efe-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="69efe-106">podczas CLRDATA_ADDRESS, w którym jest przechowywany adres pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="69efe-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="69efe-107">określoną Wskaźnik do buforu, który odbiera dane.</span><span class="sxs-lookup"><span data-stu-id="69efe-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="69efe-108">podczas Długość buforu.</span><span class="sxs-lookup"><span data-stu-id="69efe-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="69efe-109">określoną Wskaźnik do liczby zwracanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="69efe-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69efe-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69efe-110">Requirements</span></span>  
 <span data-ttu-id="69efe-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69efe-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69efe-112">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="69efe-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="69efe-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="69efe-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69efe-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69efe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69efe-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69efe-115">See also</span></span>

- [<span data-ttu-id="69efe-116">ICLRDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="69efe-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
