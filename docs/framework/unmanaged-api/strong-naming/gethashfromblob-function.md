---
title: GetHashFromBlob — Funkcja
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
ms.openlocfilehash: d1027aea1d800bda1654b223fec992aa70efd4b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140711"
---
# <a name="gethashfromblob-function"></a>GetHashFromBlob — Funkcja

Pobiera skrót zestawu pod określonym adresem pamięci przy użyciu określonego algorytmu wyznaczania wartości skrótu.

Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: GetHashFromBlob —](../hosting/iclrstrongname-gethashfromblob-method.md) .

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a>Parametry

`pbBlob`\
podczas Wskaźnik do adresu bloku pamięci, który ma zostać zmieszany.

`cchBlob`\
podczas Długość (w bajtach) bloku pamięci.

`piHashAlg`\
[in. out] Stała, która określa algorytm wyznaczania wartości skrótu. Użyj wartości zero dla algorytmu domyślnego.

`pbHash`\
określoną Zwrócony bufor wyznaczania wartości skrótu.

`cchHash`\
podczas Żądany maksymalny rozmiar `pbHash`.

`pchHash`\
określoną Rozmiar w bajtach zwracanej `pbHash`.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** StrongName. h

**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll

**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [GetHashFromBlob, metoda](../hosting/iclrstrongname-gethashfromblob-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
