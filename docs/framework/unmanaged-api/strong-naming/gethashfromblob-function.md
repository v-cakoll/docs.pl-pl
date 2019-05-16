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
ms.openlocfilehash: 6ba049723710b378a90d17c67735a05e8a09d05d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636850"
---
# <a name="gethashfromblob-function"></a>GetHashFromBlob — Funkcja

Pobiera skrót zestawu pod adresem określonym pamięci, przy użyciu określonego algorytmu skrótu.

Ta funkcja jest przestarzała. Użyj [iclrstrongname::gethashfromblob —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) metody zamiast tego.

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
[in] Wskaźnik na adres bloku pamięci, aby zostać obliczona wartość skrótu.

`cchBlob`\
[in] Długość w bajtach, bloku pamięci.

`piHashAlg`\
[out w] Stała, który określa algorytm wyznaczania wartości skrótu. Użyj wartości zero dla domyślny algorytm.

`pbHash`\
[out] Bufor zwrócone wyznaczania wartości skrótu.

`cchHash`\
[in] Żądany maksymalny rozmiar `pbHash`.

`pchHash`\
[out] Rozmiar w bajtach zwracanego `pbHash`.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** StrongName.h

**Biblioteka:** Dołączony jako zasób w MsCorEE.dll

**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [GetHashFromBlob, metoda](../hosting/iclrstrongname-gethashfromblob-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
