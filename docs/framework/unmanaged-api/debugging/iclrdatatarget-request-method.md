---
title: "ICLRDataTarget::Request — Metoda"
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
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7e7bde3a0bc26a6bc93124fa835c4203cd596906
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="c0666-102">ICLRDataTarget::Request — Metoda</span><span class="sxs-lookup"><span data-stu-id="c0666-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="c0666-103">Metoda wywoływana przez wspólne języka wspólnego (CLR) danych dostęp do usługi do żądania operacji zdefiniowanej przez implementację.</span><span class="sxs-lookup"><span data-stu-id="c0666-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0666-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0666-104">Syntax</span></span>  
  
```  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0666-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0666-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="c0666-106">[in] Zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c0666-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="c0666-107">[in] Rozmiar buforu wejściowego, który służy do żądania przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="c0666-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="c0666-108">[in] Bufor zawierający żądania.</span><span class="sxs-lookup"><span data-stu-id="c0666-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="c0666-109">[in] Rozmiar buforu wyjściowego, który służy do odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="c0666-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="c0666-110">[out] Bufor zawierający odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="c0666-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0666-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0666-111">Remarks</span></span>  
 <span data-ttu-id="c0666-112">`Request` Metoda ułatwia dodanie nieokreślony operacjach niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="c0666-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="c0666-113">Oznacza to, że ta metoda zapewnia rozszerzalności bez konieczności zmiany definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c0666-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="c0666-114">Ta metoda jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0666-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0666-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0666-115">Requirements</span></span>  
 <span data-ttu-id="c0666-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0666-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0666-117">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c0666-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c0666-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0666-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0666-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0666-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0666-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0666-120">See Also</span></span>  
 [<span data-ttu-id="c0666-121">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="c0666-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
