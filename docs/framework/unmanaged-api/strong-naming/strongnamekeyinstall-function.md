---
title: StrongNameKeyInstall — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
ms.openlocfilehash: 9e441d4da64e9704fbda2368d2b07289aaea610a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125195"
---
# <a name="strongnamekeyinstall-function"></a>StrongNameKeyInstall — Funkcja

Importuje parę kluczy publiczny/prywatny do kontenera.

Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameKeyInstall —](../hosting/iclrstrongname-strongnamekeyinstall-method.md) .

## <a name="syntax"></a>Składnia

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a>Parametry

`wszKeyContainer`\
podczas Nazwa kontenera kluczy. `wszKeyContainer` musi być niepustym ciągiem.

`pbKeyBlob`\
podczas Para kluczy binarnych.

`cbKeyBlob`\
podczas Rozmiar w bajtach `pbKeyBlob`.

## <a name="return-value"></a>Wartość zwracana

`true` po pomyślnym zakończeniu; w przeciwnym razie `false`.

## <a name="remarks"></a>Uwagi

Aby usunąć kontener kluczy, użyj funkcji [StrongNameKeyDelete —](strongnamekeydelete-function.md) .

Jeśli funkcja `StrongNameKeyInstall` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** StrongName. h

**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll

**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [StrongNameKeyInstall, metoda](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [StrongNameKeyDelete, metoda](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
