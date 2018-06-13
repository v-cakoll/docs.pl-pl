---
title: Funkcja SpawnInstance (niezarządzany wykaz interfejsów API)
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
ms.openlocfilehash: 3f8189f0adb62aa32cd0b85ca5a653aa466c7032
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460466"
---
# <a name="spawninstance-function"></a>Funkcja SpawnInstance
Tworzy nowe wystąpienie klasy.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.

`lFlags`  
[in] Zastrzeżone. Ten parametr musi wynosić 0.

`ppNewInstance`  
[out] Uzyskuje wskaźnik do nowego wystąpienia klasy. Jeśli wystąpi błąd, nowy obiekt nie jest zwracany, i `ppNewInstance` jest lewej nie mają być modyfikowane.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr` nie jest prawidłową definicją klasy i nie można zduplikować nowych wystąpień. Jest on niepełny lub go nie został zarejestrowany z zarządzania systemu Windows przez wywołanie metody [PutClassWmi](putclasswmi.md). |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do wykonania operacji. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` jest `null`. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [klasy IWbemClassObject::SpawnInstance](https://msdn.microsoft.com/library/aa391458(v=vs.85).aspx) metody.

`ptr` musi być definicją klasy uzyskana z zarządzania systemu Windows. (Należy pamiętać, że duplikowanie wystąpienia z wystąpienia jest obsługiwana, ale zwrócone wystąpienie jest pusta). Następnie możesz użyć tej definicji klasy, aby utworzyć nowe wystąpienia. Wywołanie [PutInstanceWmi](putinstancewmi.md) funkcja jest wymagana, jeśli zamierzasz zapisać wystąpienie do zarządzania systemem Windows.




Nowy obiekt zwracane w `ppNewClass` automatycznie staje się podklasą bieżącego obiektu. Nie można zastąpić to zachowanie. Brak żadnej innej metody, za pomocą którego można utworzyć podklasy (klasy pochodne).

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
