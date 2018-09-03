---
title: Usuwanie funkcji (niezarządzany wykaz interfejsów API)
description: Funkcja usuwania usuwa określonej właściwości i wszystkich jego kwalifikatory z definicji klasy modelu wspólnych informacji.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 791e75aa60fd651dde1555339e31664a3523e1eb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43479867"
---
# <a name="delete-function"></a>Usuwanie funkcji
Usuwa określoną właściwość i wszystkich jego kwalifikatory z definicji klasy modelu wspólnych informacji.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`wszName`  
[in] Nazwa właściwości do usunięcia. `wszName` musi być wskaźnikiem do prawidłowego `LPCWSTR`.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Nie można usunąć właściwości. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszzName` jest nieprawidłowy. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Określona właściwość nie istnieje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci do ukończenia tej operacji. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | Właściwość jest dziedziczona z klasy bazowej. |
| `WBEM_E_SYSTEM_PROPERTY` | | Właściwość jest właściwością systemu. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | Funkcja usunięte wartość domyślną zastępowania bieżącej klasy. Wartość domyślna tej właściwości w klasie nadrzędnej została reactiviated. | 

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
