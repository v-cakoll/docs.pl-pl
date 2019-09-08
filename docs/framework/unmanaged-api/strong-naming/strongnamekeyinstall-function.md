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
ms.openlocfilehash: 353898b72f41acd0c49a43ff05e54f61b99444c4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798993"
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
podczas Nazwa kontenera kluczy. `wszKeyContainer`nie może być pustym ciągiem.

`pbKeyBlob`\
podczas Para kluczy binarnych.

`cbKeyBlob`\
podczas Rozmiar, w bajtach, z `pbKeyBlob`.

## <a name="return-value"></a>Wartość zwracana

`true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`

## <a name="remarks"></a>Uwagi

Aby usunąć kontener kluczy, użyj funkcji [StrongNameKeyDelete —](strongnamekeydelete-function.md) .

Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameKeyInstall`

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówki** StrongName.h

**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll

**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [StrongNameKeyInstall, metoda](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [StrongNameKeyDelete, metoda](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
