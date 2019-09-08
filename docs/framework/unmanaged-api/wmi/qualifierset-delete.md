---
title: QualifierSet_Delete — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja QualifierSet_Delete usuwa kwalifikator według nazwy.
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
ms.openlocfilehash: 4bc26a16650a5beecc17898e0421e79536713deb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798337"
---
# <a name="qualifierset_delete-function"></a>QualifierSet_Delete, funkcja
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
podczas Ten parametr jest nieużywany.

`ptr`   
podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`wszName`   
podczas Nazwa kwalifikatora do usunięcia.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` Parametr jest nieprawidłowy. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | Usuwanie tego kwalifikatora jest niedozwolone. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nie znaleziono określonego kwalifikatora. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | Zastępowanie lokalne zostało usunięte, a oryginalny kwalifikator z obiektu nadrzędnego został wznowiony. |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemQualifierSet::D Usuń](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) .

Ze względu na reguły propagacji kwalifikatora, określony kwalifikator może być Dziedziczony z innego obiektu i jedynie zastępowany w bieżącej klasie lub wystąpieniu. W takim przypadku `QualifierSet_Delete` metoda resetuje kwalifikator do pierwotnej dziedziczonej wartości. Funkcja w tym przypadku zwraca kod `WBEM_S_RESET_TO_DEFAULT`stanu.

## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** WMINet_Utils.idl  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
