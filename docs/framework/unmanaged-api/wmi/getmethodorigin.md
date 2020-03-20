---
title: GetMethodOrigin, funkcja (odwołanie do niezarządzanego interfejsu API)
description: Funkcja GetMethodOrigin określa klasę, w której zadeklarowana jest metoda.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5b4609b6649be875aea7dfcf52ba36b1e98ab7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176802"
---
# <a name="getmethodorigin-function"></a>GetMethodOrigin, funkcja
Określa klasę, w której metoda jest zadeklarowana.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[w] Ten parametr jest nieużywane.

`ptr`  
[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszMethodName`  
[w] Nazwa metody dla obiektu, którego klasa będąca właścicielem jest żądana.

`pstrClassName`  
[na zewnątrz] Odbiera nazwę klasy, która jest właścicielem metody.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nie znaleziono określonej metody. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Co najmniej jeden parametr jest nieprawidłowy. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [metody IWbemClassObject::GetMethodOrigin.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)

Ponieważ klasa może dziedziczyć metody z jednej lub więcej klas podstawowych, deweloperzy często chcą określić klasę, w której zdefiniowano daną metodę.

Parametr `pstrClassName` nie może wskazywać `BSTR` prawidłowe przed wywołane funkcji, ponieważ jest to `out` parametr; ten wskaźnik nie jest cofnięty po powrocie funkcji.

## <a name="requirements"></a>Wymagania  
**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
