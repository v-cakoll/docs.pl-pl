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
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream — Metoda

Tworzy strumień o określonej nazwie i formacie.

## <a name="syntax"></a>Składnia

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

## <a name="parameters"></a>Parametry

`dwFlags`\
podczas Flagi zdefiniowane w pliku Fusion. idl.

`pszStreamName`\
podczas Nazwa strumienia, który ma zostać utworzony.

`dwFormat`\
podczas Format pliku, który ma być przesyłany strumieniowo.

`dwFormatFlags`\
podczas Flagi specyficzne dla formatu zdefiniowane w pliku Fusion. idl.

`ppIStream`\
określoną Wskaźnik do adresu zwróconego wystąpienia [IStream](/windows/desktop/api/objidl/nn-objidl-istream) .

`puliMaxSize`\
[w, opcjonalnie] Maksymalny rozmiar strumienia, do którego odwołuje się `ppIStream`.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** Fusion. h

**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [IAssemblyCacheItem, interfejs](iassemblycacheitem-interface.md)
