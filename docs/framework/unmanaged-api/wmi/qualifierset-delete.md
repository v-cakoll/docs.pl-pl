---
title: Funkcja QualifierSet_Delete (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_Delete powoduje usunięcie kwalifikatorze według nazwy.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 956abe8ddf8075b7b8f8c057db0aa7187982e1d5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782608"
---
# <a name="qualifiersetdelete-function"></a>QualifierSet_Delete — funkcja
Usuwa określony kwalifikator według nazwy.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr jest nieużywany.

`ptr`   
[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.

`wszName`   
[in] Nazwa kwalifikatora do usunięcia.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` Parametr jest nieprawidłowy. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | Usunięcie tego kwalifikatora jest niedozwolone. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nie można odnaleźć określonego kwalifikator. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | Zastąpienie lokalnych została usunięta i oryginalny kwalifikator z obiektu nadrzędnego wznowił zakresu. |

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) metody.

Ze względu na zasady propagacji kwalifikator kwalifikator określonego może zostały odziedziczone z innym obiektem i jedynie zastąpione w bieżącej klasy lub wystąpienia. W tym przypadku `QualifierSet_Delete` metoda powoduje zresetowanie kwalifikator do oryginalnej wartości dziedziczone. Funkcja w takiej sytuacji zwraca kod stanu `WBEM_S_RESET_TO_DEFAULT`.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
