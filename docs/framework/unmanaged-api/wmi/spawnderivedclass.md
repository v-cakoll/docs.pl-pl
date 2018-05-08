---
title: Funkcja SpawnDerivedClass (niezarządzany wykaz interfejsów API)
description: Funkcja SpawnDerivedClass tworzy nowy obiekt, który pochodzi z obiektu.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe93b7ee28db8151345871b0dd716d41227ed565
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="spawnderivedclass-function"></a>Funkcja SpawnDerivedClass
Tworzy obiekt klasy pochodnej nowo od określonego obiektu.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.

`lFlags`  
[in] Zastrzeżone. Ten parametr musi wynosić 0.

`ppNewClass`  
[out] Uzyskuje wskaźnik do nowego obiektu definicji klasy. Jeśli wystąpi błąd, nowy obiekt nie jest zwracany, i `ppNewClass` jest lewej nie mają być modyfikowane. Wartość nie może być `null`.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Zażądano nieprawidłową operację, takiej jak duplikowanie klasy z wystąpienia. |
| `WBEM_E_INCOMPLETE_CLASS` | Klasa źródłowa całkowicie nie została zdefiniowana lub jest zarejestrowana w usłudze zarządzania systemu Windows, więc nowej klasy pochodnej nie jest dozwolone. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do wykonania operacji. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` jest `null`. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) metody.

`ptr` musi być definicją klasy, która staje się klasy nadrzędnej uruchomionego obiektu. Zwrócony obiekt staje się podklasą bieżącego obiektu.

Nowy obiekt zwracane w `ppNewClass` automatycznie staje się podklasą bieżącego obiektu. Nie można zastąpić to zachowanie. Brak żadnej innej metody, za pomocą którego można utworzyć podklasy (klasy pochodne).

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
