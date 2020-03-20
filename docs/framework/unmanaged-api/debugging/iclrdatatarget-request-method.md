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
ms.openlocfilehash: 336ba38bc80fcb2649a12c78691e52c5e4d70bfe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179114"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="a32ef-102">ICLRDataTarget::Request — Metoda</span><span class="sxs-lookup"><span data-stu-id="a32ef-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="a32ef-103">Wywoływane przez usługi dostępu do danych środowiska wykonawczego języka wspólnego (CLR) do żądania operacji, zgodnie z definicją implementacji.</span><span class="sxs-lookup"><span data-stu-id="a32ef-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a32ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a32ef-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="a32ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a32ef-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="a32ef-106">[w] Zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a32ef-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="a32ef-107">[w] Rozmiar buforu wejściowego, który jest używany dla żądania przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="a32ef-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="a32ef-108">[w] Bufor zawierający żądanie.</span><span class="sxs-lookup"><span data-stu-id="a32ef-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="a32ef-109">[w] Rozmiar buforu wyjściowego, który jest używany dla odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a32ef-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="a32ef-110">[na zewnątrz] Bufor zawierający odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="a32ef-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a32ef-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a32ef-111">Remarks</span></span>  
 <span data-ttu-id="a32ef-112">Metoda `Request` ułatwia dodawanie nieokreślonych operacji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a32ef-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="a32ef-113">Oznacza to, że ta metoda zapewnia rozszerzalność bez konieczności zmiany definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a32ef-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="a32ef-114">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="a32ef-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a32ef-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a32ef-115">Requirements</span></span>  
 <span data-ttu-id="a32ef-116">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a32ef-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a32ef-117">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="a32ef-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a32ef-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a32ef-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a32ef-119">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a32ef-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a32ef-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a32ef-120">See also</span></span>

- [<span data-ttu-id="a32ef-121">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="a32ef-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
