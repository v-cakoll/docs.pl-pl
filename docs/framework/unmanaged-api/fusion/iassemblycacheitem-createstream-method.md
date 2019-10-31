---
title: IAssemblyCacheItem::CreateStream — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
ms.openlocfilehash: 0660621f465f2ba3610e06bd1df38baa1bc5c907
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134472"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="6069f-102">IAssemblyCacheItem::CreateStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="6069f-102">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="6069f-103">Tworzy strumień o określonej nazwie i formacie.</span><span class="sxs-lookup"><span data-stu-id="6069f-103">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="6069f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6069f-104">Syntax</span></span>

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a><span data-ttu-id="6069f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6069f-105">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="6069f-106">podczas Flagi zdefiniowane w pliku Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="6069f-106">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="6069f-107">podczas Nazwa strumienia, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="6069f-107">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="6069f-108">podczas Format pliku, który ma być przesyłany strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="6069f-108">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="6069f-109">podczas Flagi specyficzne dla formatu zdefiniowane w pliku Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="6069f-109">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="6069f-110">określoną Wskaźnik do adresu zwróconego wystąpienia [IStream](/windows/desktop/api/objidl/nn-objidl-istream) .</span><span class="sxs-lookup"><span data-stu-id="6069f-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="6069f-111">[w, opcjonalnie] Maksymalny rozmiar strumienia, do którego odwołuje się `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="6069f-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="6069f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6069f-112">Requirements</span></span>

<span data-ttu-id="6069f-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6069f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="6069f-114">**Nagłówek:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="6069f-114">**Header:** Fusion.h</span></span>

<span data-ttu-id="6069f-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6069f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6069f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6069f-116">See also</span></span>

- [<span data-ttu-id="6069f-117">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="6069f-117">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
