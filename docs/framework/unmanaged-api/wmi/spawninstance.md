---
title: SpawnInstance, funkcja (odwołanie do interfejsu API niezarządzanego)
description: SpawnInstance Funkcja tworzy nowe wystąpienie klasy.
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
ms.openlocfilehash: a15eb8123c1ee807444bdb4c6fe71cdccc08f434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176724"
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
[w] Ten parametr jest nieużywane.

`ptr`  
[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lFlags`  
[w] Zastrzeżone. Ten parametr musi być 0.

`ppNewInstance`  
[na zewnątrz] Odbiera wskaźnik do nowego wystąpienia klasy. Jeśli wystąpi błąd, nowy obiekt nie `ppNewInstance` jest zwracany i pozostaje niezmodyfikowany.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | `ptr`nie jest prawidłową definicją klasy i nie może zrodzić nowych wystąpień. Albo jest niekompletny lub nie został zarejestrowany w usłudze Windows Management, wywołując [PutClassWmi](putclasswmi.md). |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do ukończenia operacji. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr `ppNewClass` ma wartość `null`. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [metody IWbemClassObject::SpawnInstance.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance)

`ptr`musi być definicją klasy uzyskaną z zarządzania systemem Windows. (Należy zauważyć, że tarło wystąpienia z wystąpienia jest obsługiwane, ale zwrócone wystąpienie jest puste.) Następnie należy użyć tej definicji klasy do tworzenia nowych wystąpień. Wywołanie funkcji [PutInstanceWmi](putinstancewmi.md) jest wymagane, jeśli zamierzasz zapisać wystąpienie w usłudze Windows Management.

Nowy obiekt zwracany automatycznie `ppNewClass` staje się podklasą bieżącego obiektu. Tego zachowania nie można zastąpić. Nie ma innej metody, za pomocą której można tworzyć podklasy (klasy pochodne).

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
