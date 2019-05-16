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
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream — Metoda

Tworzy strumień o określonej nazwie i format.

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
[in] Flagi zdefiniowane w Fusion.idl.

`pszStreamName`\
[in] Nazwa strumienia, który ma zostać utworzony.

`dwFormat`\
[in] Format pliku do celów przesyłania strumieniowego.

`dwFormatFlags`\
[in] Zdefiniowane w Fusion.idl flagi specyficzne dla formatu.

`ppIStream`\
[out] Wskaźnik na adres zwracanego [IStream](/windows/desktop/api/objidl/nn-objidl-istream) wystąpienia.

`puliMaxSize`\
[in, opcjonalny] Maksymalny rozmiar strumienia odwołuje się `ppIStream`.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** Fusion.h

**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [IAssemblyCacheItem, interfejs](iassemblycacheitem-interface.md)
