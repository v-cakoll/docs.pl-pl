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
ms.openlocfilehash: 74eb098ee68f57477c8b9115db2bce60919f0b12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580216"
---
# <a name="spawninstance-function"></a>SpawnInstance — funkcja
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
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`lFlags`  
[in] Zastrzeżone. Ten parametr musi być 0.

`ppNewInstance`  
[out] Otrzymuje wskaźnik do nowego wystąpienia klasy. Jeśli wystąpi błąd, nowy obiekt nie jest zwracana, i `ppNewInstance` się po lewej stronie w niezmienionej postaci.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr` nie jest prawidłową definicją klasy i nie można zduplikować nowych wystąpień. Jest on niepełny lub go nie został zarejestrowany za pomocą funkcji zarządzania Windows, wywołując [PutClassWmi](putclasswmi.md). |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` jest `null`. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [klasy IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) metody.

`ptr` musi być definicją klasy uzyskana z zarządzania Windows. (Należy pamiętać, że podczas duplikowania wystąpienie z wystąpienia usługi jest obsługiwany, ale zwracane wystąpienie jest puste). Następnie możesz użyć tej definicji klasy, do tworzenia nowych wystąpień. Wywołanie [PutInstanceWmi](putinstancewmi.md) funkcja jest wymagana, jeśli zamierzasz zapisać wystąpienie zarządzania Windows.




Nowy obiekt zwrócony w `ppNewClass` automatycznie wybrana zostaje pierwsza podklasę bieżącego obiektu. Nie można zastąpić to zachowanie. Nie ma żadnej innej metody, za pomocą którego można utworzyć podklasy (klas pochodnych).

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
