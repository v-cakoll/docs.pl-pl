---
title: SpawnDerivedClass, funkcja (odwołanie do niezarządzanego interfejsu API)
description: SpawnDerivedClass Funkcja tworzy nowy obiekt, który pochodzi z obiektu.
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
ms.openlocfilehash: e9784f8a024c788823dc702794b2b86eea1827bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174852"
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass, funkcja
Tworzy nowo pochodny obiekt klasy z określonego obiektu.
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[w] Ten parametr jest nieużywane.

`ptr`  
[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lFlags`  
[w] Zastrzeżone. Ten parametr musi być 0.

`ppNewClass`  
[na zewnątrz] Odbiera wskaźnik do nowego obiektu definicji klasy. Jeśli wystąpi błąd, nowy obiekt nie `ppNewClass` jest zwracany i pozostaje niezmodyfikowany. Jego wartość `null`nie może być .

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpiła ogólna porażka. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Zażądano nieprawidłowej operacji, takiej jak tarło klasy z wystąpienia. |
| `WBEM_E_INCOMPLETE_CLASS` | Klasa źródłowsza nie została całkowicie zdefiniowana lub zarejestrowana w programie Windows Management, więc nowa klasa pochodna nie jest dozwolona. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do ukończenia operacji. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr `ppNewClass` ma wartość `null`. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [metody IWbemClassObject::SpawnDerivedClass.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)

`ptr`musi być definicją klasy, która staje się klasą nadrzędną obiektu zduplikowanego. Zwrócony obiekt staje się podklasą bieżącego obiektu.

Nowy obiekt zwracany automatycznie `ppNewClass` staje się podklasą bieżącego obiektu. Tego zachowania nie można zastąpić. Nie ma innej metody, za pomocą której można tworzyć podklasy (klasy pochodne).

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
