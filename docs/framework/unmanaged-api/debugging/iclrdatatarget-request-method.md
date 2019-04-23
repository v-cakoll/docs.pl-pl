---
title: ICLRDataTarget::Request — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9005dd8fde0d7258bd1dd48b561e4925e87733b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102697"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="2d7e2-102">ICLRDataTarget::Request — Metoda</span><span class="sxs-lookup"><span data-stu-id="2d7e2-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="2d7e2-103">Metoda wywoływana przez wspólnego języka wspólnego (CLR) usługi dostępu do danych do żądania operacji, zgodnie z definicją przez implementację.</span><span class="sxs-lookup"><span data-stu-id="2d7e2-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d7e2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d7e2-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2d7e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d7e2-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="2d7e2-106">[in] Zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2d7e2-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="2d7e2-107">[in] Rozmiar buforu wejściowego, który służy do żądania przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="2d7e2-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="2d7e2-108">[in] Bufor zawierający żądania.</span><span class="sxs-lookup"><span data-stu-id="2d7e2-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="2d7e2-109">[in] Rozmiar buforu wyjściowego, który służy do odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2d7e2-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="2d7e2-110">[out] Bufor, zawierająca odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="2d7e2-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d7e2-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d7e2-111">Remarks</span></span>  
 <span data-ttu-id="2d7e2-112">`Request` Metoda ułatwia dodawanie nieokreślony operacjach niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="2d7e2-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="2d7e2-113">Oznacza to, że ta metoda zapewnia rozszerzalność bez konieczności zmiany definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2d7e2-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="2d7e2-114">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2d7e2-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d7e2-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d7e2-115">Requirements</span></span>  
 <span data-ttu-id="2d7e2-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d7e2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d7e2-117">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2d7e2-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2d7e2-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d7e2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d7e2-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d7e2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d7e2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d7e2-120">See also</span></span>

- [<span data-ttu-id="2d7e2-121">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="2d7e2-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
