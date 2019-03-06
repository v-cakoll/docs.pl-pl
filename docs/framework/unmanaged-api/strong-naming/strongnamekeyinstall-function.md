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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b3fc69b2edf611383402b13555cf33be10dbad3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366585"
---
# <a name="strongnamekeyinstall-function"></a>StrongNameKeyInstall — Funkcja

Importuje pary kluczy publiczny/prywatny w kontenerze.

Ta funkcja jest przestarzała. Użyj [iclrstrongname::strongnamekeyinstall —](../hosting/iclrstrongname-strongnamekeyinstall-method.md) metody zamiast tego.

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
[in] Nazwa kontenera kluczy. `wszKeyContainer` musi być ciągiem niepustym.

`pbKeyBlob`\
[in] Binarny pary kluczy.

`cbKeyBlob`\
[in] Rozmiar w bajtach z `pbKeyBlob`.

## <a name="return-value"></a>Wartość zwracana

`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.

## <a name="remarks"></a>Uwagi

Użyj [StrongNameKeyDelete](strongnamekeydelete-function.md) funkcję, aby usunąć kontener kluczy.

Jeśli `StrongNameKeyInstall` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** StrongName.h

**Biblioteka:** Dołączony jako zasób w MsCorEE.dll

**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [StrongNameKeyInstall, metoda](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [StrongNameKeyDelete, metoda](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)