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
ms.openlocfilehash: a98273307003485202d8c12d5c27fda04ff5a0ae
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629876"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="b8c5b-102">IAssemblyCacheItem::CreateStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="b8c5b-102">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="b8c5b-103">Tworzy strumień o określonej nazwie i format.</span><span class="sxs-lookup"><span data-stu-id="b8c5b-103">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8c5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8c5b-104">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="b8c5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8c5b-105">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="b8c5b-106">[in] Flagi zdefiniowane w Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="b8c5b-106">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="b8c5b-107">[in] Nazwa strumienia, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="b8c5b-107">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="b8c5b-108">[in] Format pliku do celów przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="b8c5b-108">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="b8c5b-109">[in] Zdefiniowane w Fusion.idl flagi specyficzne dla formatu.</span><span class="sxs-lookup"><span data-stu-id="b8c5b-109">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="b8c5b-110">[out] Wskaźnik na adres zwracanego [IStream](/windows/desktop/api/objidl/nn-objidl-istream) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b8c5b-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="b8c5b-111">[in, opcjonalny] Maksymalny rozmiar strumienia odwołuje się `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="b8c5b-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8c5b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8c5b-112">Requirements</span></span>

<span data-ttu-id="b8c5b-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8c5b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="b8c5b-114">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b8c5b-114">**Header:** Fusion.h</span></span>

<span data-ttu-id="b8c5b-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8c5b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b8c5b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8c5b-116">See also</span></span>

- [<span data-ttu-id="b8c5b-117">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="b8c5b-117">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
