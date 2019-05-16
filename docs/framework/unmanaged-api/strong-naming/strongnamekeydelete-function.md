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
ms.openlocfilehash: 717d2104db8addf40e5187cee4cc8c46e5dc355e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636737"
---
# <a name="strongnamekeydelete-function"></a>StrongNameKeyDelete — Funkcja

Usuwa określony kontener kluczy.

Ta funkcja jest przestarzała. Użyj [iclrstrongname::strongnamekeydelete —](../hosting/iclrstrongname-strongnamekeydelete-method.md) metody zamiast tego.

## <a name="syntax"></a>Składnia

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a>Parametry

`wszKeyContainer`\
[in] Nazwa kontenera kluczy do usunięcia.

## <a name="return-value"></a>Wartość zwracana

`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.

## <a name="remarks"></a>Uwagi

Użyj [StrongNameKeyInstall](strongnamekeyinstall-function.md) funkcji do zaimportowania pary kluczy publiczny/prywatny w kontenerze.

Jeśli `StrongNameKeyDelete` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** StrongName.h

**Biblioteka:** Dołączony jako zasób w MsCorEE.dll

**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [StrongNameKeyDelete, metoda](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [StrongNameKeyInstall, metoda](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
