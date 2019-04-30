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