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
ms.openlocfilehash: 380e248c8c4e3407fff868cdd9a5c63b63e50c69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697516"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="5e4ec-102">IAssemblyCacheItem::CreateStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e4ec-102">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="5e4ec-103">Tworzy strumień o określonej nazwie i format.</span><span class="sxs-lookup"><span data-stu-id="5e4ec-103">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="5e4ec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e4ec-104">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="5e4ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e4ec-105">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="5e4ec-106">[in] Flagi zdefiniowane w Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="5e4ec-106">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="5e4ec-107">[in] Nazwa strumienia, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="5e4ec-107">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="5e4ec-108">[in] Format pliku do celów przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="5e4ec-108">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="5e4ec-109">[in] Zdefiniowane w Fusion.idl flagi specyficzne dla formatu.</span><span class="sxs-lookup"><span data-stu-id="5e4ec-109">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="5e4ec-110">[out] Wskaźnik na adres zwracanego [IStream](/windows/desktop/api/objidl/nn-objidl-istream) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5e4ec-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="5e4ec-111">[in, opcjonalny] Maksymalny rozmiar strumienia odwołuje się `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="5e4ec-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="5e4ec-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e4ec-112">Requirements</span></span>

<span data-ttu-id="5e4ec-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e4ec-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="5e4ec-114">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="5e4ec-114">**Header:** Fusion.h</span></span>

<span data-ttu-id="5e4ec-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e4ec-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5e4ec-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e4ec-116">See also</span></span>

- [<span data-ttu-id="5e4ec-117">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e4ec-117">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)