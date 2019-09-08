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
[w, opcjonalnie] Maksymalny rozmiar strumienia, do którego odwołuje `ppIStream`się.

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówki** Fusion. h

**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [IAssemblyCacheItem, interfejs](iassemblycacheitem-interface.md)
