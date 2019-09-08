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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59b4df08157ce14a58393e54b671e8f41b8998ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799230"
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
określoną Rozmiar zwracanych `pbHash`wartości (w bajtach).

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówki** StrongName.h

**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll

**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [GetHashFromBlob, metoda](../hosting/iclrstrongname-gethashfromblob-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
