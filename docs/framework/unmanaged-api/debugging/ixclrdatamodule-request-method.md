---
title: Metoda IXCLRDataModule::Request
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0226a11b142515296d976e3d645cb2475d634420
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416150"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="0218c-102">Metoda IXCLRDataModule::Request</span><span class="sxs-lookup"><span data-stu-id="0218c-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="0218c-103">Żądania do buforu, biorąc pod uwagę przy użyciu danych modułu wypełniania.</span><span class="sxs-lookup"><span data-stu-id="0218c-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0218c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0218c-104">Syntax</span></span>
```
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

### <a name="parameters"></a><span data-ttu-id="0218c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0218c-105">Parameters</span></span>

<span data-ttu-id="0218c-106">`reqCode` [in] Typ do wysłania żądania.</span><span class="sxs-lookup"><span data-stu-id="0218c-106">`reqCode` [in] Request type to be sent.</span></span>

<span data-ttu-id="0218c-107">`inBufferSize` [in] rozmiar buforu wejściowego, który ma być przekazany w.</span><span class="sxs-lookup"><span data-stu-id="0218c-107">`inBufferSize` [in] size of the input buffer to be passed in.</span></span>

<span data-ttu-id="0218c-108">`inBuffer` [in, size_is(inBufferSize)] Bufor wskaźnik do danych pierwotnych, które mają być wysyłane w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="0218c-108">`inBuffer` [in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

<span data-ttu-id="0218c-109">`outBufferSize` [in] Rozmiar buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="0218c-109">`outBufferSize` [in] Size of the output buffer.</span></span>

<span data-ttu-id="0218c-110">`outBuffer` [out, size_is(outBufferSize)] Wskaźnik buforu używany do przechowywania odpowiedzi na żądanie.</span><span class="sxs-lookup"><span data-stu-id="0218c-110">`outBuffer` [out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="0218c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0218c-111">Remarks</span></span>

<span data-ttu-id="0218c-112">Podana metoda jest częścią `IXCLRDataModule` interfejs i odnosi się do 36 gniazda tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="0218c-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 36th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0218c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0218c-113">Requirements</span></span>

<span data-ttu-id="0218c-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0218c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0218c-115">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="0218c-115">**Header:** None</span></span>   
<span data-ttu-id="0218c-116">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="0218c-116">**Library:** None</span></span>  
<span data-ttu-id="0218c-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0218c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0218c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0218c-118">See Also</span></span>
- [<span data-ttu-id="0218c-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0218c-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="0218c-120">Interfejs IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="0218c-120">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)