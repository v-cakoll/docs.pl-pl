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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5af7dc4e1694b66fc4a5ce37e515c71e9fa3db49
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796733"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="1b47f-102">IAssemblyCacheItem::CreateStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b47f-102">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="1b47f-103">Tworzy strumień o określonej nazwie i formacie.</span><span class="sxs-lookup"><span data-stu-id="1b47f-103">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b47f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b47f-104">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="1b47f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b47f-105">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="1b47f-106">podczas Flagi zdefiniowane w pliku Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="1b47f-106">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="1b47f-107">podczas Nazwa strumienia, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="1b47f-107">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="1b47f-108">podczas Format pliku, który ma być przesyłany strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="1b47f-108">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="1b47f-109">podczas Flagi specyficzne dla formatu zdefiniowane w pliku Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="1b47f-109">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="1b47f-110">określoną Wskaźnik do adresu zwróconego wystąpienia [IStream](/windows/desktop/api/objidl/nn-objidl-istream) .</span><span class="sxs-lookup"><span data-stu-id="1b47f-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="1b47f-111">[w, opcjonalnie] Maksymalny rozmiar strumienia, do którego odwołuje `ppIStream`się.</span><span class="sxs-lookup"><span data-stu-id="1b47f-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b47f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b47f-112">Requirements</span></span>

<span data-ttu-id="1b47f-113">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b47f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1b47f-114">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="1b47f-114">**Header:** Fusion.h</span></span>

<span data-ttu-id="1b47f-115">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b47f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1b47f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b47f-116">See also</span></span>

- [<span data-ttu-id="1b47f-117">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b47f-117">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
