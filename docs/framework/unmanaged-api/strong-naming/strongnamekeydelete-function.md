---
title: StrongNameKeyDelete — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
ms.openlocfilehash: d37f990241ae704abef55d863da0f40a31284837
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141585"
---
# <a name="strongnamekeydelete-function"></a>StrongNameKeyDelete — Funkcja

Usuwa określony kontener kluczy.

Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameKeyDelete —](../hosting/iclrstrongname-strongnamekeydelete-method.md) .

## <a name="syntax"></a>Składnia

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a>Parametry

`wszKeyContainer`\
podczas Nazwa kontenera kluczy do usunięcia.

## <a name="return-value"></a>Wartość zwracana

`true` po pomyślnym zakończeniu; w przeciwnym razie `false`.

## <a name="remarks"></a>Uwagi

Użyj funkcji [StrongNameKeyInstall —](strongnamekeyinstall-function.md) , aby zaimportować parę kluczy publicznych/prywatnych do kontenera.

Jeśli funkcja `StrongNameKeyDelete` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** StrongName. h

**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll

**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [StrongNameKeyDelete, metoda](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall, metoda](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
