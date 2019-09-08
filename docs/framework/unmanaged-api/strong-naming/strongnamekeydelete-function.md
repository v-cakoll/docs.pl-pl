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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17d35193f69966e02ac5e483924fcb3ee2e06758
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799023"
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

`true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`

## <a name="remarks"></a>Uwagi

Użyj funkcji [StrongNameKeyInstall —](strongnamekeyinstall-function.md) , aby zaimportować parę kluczy publicznych/prywatnych do kontenera.

Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameKeyDelete`

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówki** StrongName.h

**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll

**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [StrongNameKeyDelete, metoda](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall, metoda](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
