---
title: SpawnInstance — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja SpawnInstance tworzy nowe wystąpienie klasy.
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 529905bd9286520a8e09479bfc95ef0b614f53e9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798221"
---
# <a name="spawninstance-function"></a>SpawnInstance, funkcja
Tworzy nowe wystąpienie klasy.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
podczas Ten parametr jest nieużywany.

`ptr`  
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lFlags`  
podczas Rezerwacj. Ten parametr musi być równy 0.

`ppNewInstance`  
określoną Odbiera wskaźnik do nowego wystąpienia klasy. Jeśli wystąpi błąd, nowy obiekt nie jest zwracany i `ppNewInstance` pozostaje niemodyfikowany.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr`nie jest prawidłową definicją klasy i nie można zduplikować nowych wystąpień. Jest on niekompletny lub nie został zarejestrowany w usłudze Windows Management przez wywołanie [PutClassWmi](putclasswmi.md). |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby ukończyć tę operację. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass`jest `null`. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject:: SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) .

`ptr`musi być definicją klasy uzyskaną z zarządzania systemem Windows. (Należy zauważyć, że duplikowanie wystąpienia z wystąpienia jest obsługiwane, ale zwrócone wystąpienie jest puste). Następnie należy użyć tej definicji klasy do tworzenia nowych wystąpień. Wywołanie funkcji [PutInstanceWmi](putinstancewmi.md) jest wymagane, jeśli zamierzasz napisać wystąpienie do zarządzania systemem Windows.

Nowy obiekt zwrócony w programie `ppNewClass` automatycznie zostanie podklasą bieżącego obiektu. Tego zachowania nie można zastąpić. Nie istnieje inna metoda, za pomocą której można tworzyć podklasy (klasy pochodne).

## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** WMINet_Utils.idl  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
