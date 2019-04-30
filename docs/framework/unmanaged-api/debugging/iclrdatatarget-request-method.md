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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698073"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="f5338-102">ICLRDataTarget::Request — Metoda</span><span class="sxs-lookup"><span data-stu-id="f5338-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="f5338-103">Metoda wywoływana przez wspólnego języka wspólnego (CLR) usługi dostępu do danych do żądania operacji, zgodnie z definicją przez implementację.</span><span class="sxs-lookup"><span data-stu-id="f5338-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5338-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5338-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f5338-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5338-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="f5338-106">[in] Zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f5338-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="f5338-107">[in] Rozmiar buforu wejściowego, który służy do żądania przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="f5338-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="f5338-108">[in] Bufor zawierający żądania.</span><span class="sxs-lookup"><span data-stu-id="f5338-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="f5338-109">[in] Rozmiar buforu wyjściowego, który służy do odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f5338-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="f5338-110">[out] Bufor, zawierająca odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="f5338-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5338-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5338-111">Remarks</span></span>  
 <span data-ttu-id="f5338-112">`Request` Metoda ułatwia dodawanie nieokreślony operacjach niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="f5338-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="f5338-113">Oznacza to, że ta metoda zapewnia rozszerzalność bez konieczności zmiany definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f5338-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="f5338-114">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5338-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5338-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5338-115">Requirements</span></span>  
 <span data-ttu-id="f5338-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5338-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5338-117">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f5338-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f5338-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5338-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5338-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5338-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5338-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5338-120">See also</span></span>

- [<span data-ttu-id="f5338-121">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5338-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
