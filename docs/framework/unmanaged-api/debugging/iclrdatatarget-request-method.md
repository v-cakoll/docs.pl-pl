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
ms.openlocfilehash: e5d7a6b9826a734363d6beeb2e3fab8422964558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113352"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="14765-102">ICLRDataTarget::Request — Metoda</span><span class="sxs-lookup"><span data-stu-id="14765-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="14765-103">Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) do żądania operacji zgodnie z definicją w implementacji.</span><span class="sxs-lookup"><span data-stu-id="14765-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14765-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14765-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="14765-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14765-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="14765-106">podczas Zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="14765-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="14765-107">podczas Rozmiar buforu wejściowego, który jest używany w żądaniu przychodzącym.</span><span class="sxs-lookup"><span data-stu-id="14765-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="14765-108">podczas Bufor zawierający żądanie.</span><span class="sxs-lookup"><span data-stu-id="14765-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="14765-109">podczas Rozmiar buforu wyjściowego, który jest używany na potrzeby odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="14765-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="14765-110">określoną Bufor zawierający odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="14765-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14765-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14765-111">Remarks</span></span>  
 <span data-ttu-id="14765-112">Metoda `Request` ułatwia dodawanie nieokreślonych operacji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="14765-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="14765-113">Oznacza to, że ta metoda zapewnia rozszerzalność bez konieczności zmiany definicji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="14765-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="14765-114">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="14765-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14765-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14765-115">Requirements</span></span>  
 <span data-ttu-id="14765-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14765-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14765-117">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="14765-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="14765-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="14765-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14765-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14765-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14765-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14765-120">See also</span></span>

- [<span data-ttu-id="14765-121">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="14765-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
