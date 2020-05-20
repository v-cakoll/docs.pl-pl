---
title: 'IXCLRDataModule:: Request — Metoda'
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
ms.openlocfilehash: 3c18fc5c947cbb89fc4e9aed60d3cedcbe22d749
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420815"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="d9e9c-102">IXCLRDataModule:: Request — Metoda</span><span class="sxs-lookup"><span data-stu-id="d9e9c-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="d9e9c-103">Żądania wypełnienia buforu podanego za pomocą danych modułu.</span><span class="sxs-lookup"><span data-stu-id="d9e9c-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d9e9c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9e9c-104">Syntax</span></span>

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="d9e9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9e9c-105">Parameters</span></span>

`reqCode`\
<span data-ttu-id="d9e9c-106">podczas Typ żądania do wysłania.</span><span class="sxs-lookup"><span data-stu-id="d9e9c-106">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="d9e9c-107">[in] rozmiar buforu wejściowego, który ma zostać przesłany.</span><span class="sxs-lookup"><span data-stu-id="d9e9c-107">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="d9e9c-108">[in, size_is (inBufferSize)] Wskaźnik buforu dla nieprzetworzonych danych, które mają zostać wysłane w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="d9e9c-108">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="d9e9c-109">podczas Rozmiar buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d9e9c-109">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="d9e9c-110">[out, size_is (outBufferSize)] Wskaźnik buforu używany do przechowywania odpowiedzi na żądanie.</span><span class="sxs-lookup"><span data-stu-id="d9e9c-110">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9e9c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9e9c-111">Remarks</span></span>

<span data-ttu-id="d9e9c-112">Podana metoda jest częścią `IXCLRDataModule` interfejsu i odpowiada gnieździe 37th tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="d9e9c-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 37th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d9e9c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9e9c-113">Requirements</span></span>

<span data-ttu-id="d9e9c-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9e9c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="d9e9c-115">**Nagłówek:** Brak **biblioteki:** brak **.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d9e9c-115">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d9e9c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9e9c-116">See also</span></span>

- [<span data-ttu-id="d9e9c-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d9e9c-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="d9e9c-118">IXCLRDataModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9e9c-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
