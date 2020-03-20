---
title: funkcja QualifierSet_Delete (odwołanie do interfejsu API niezarządzanego)
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
ms.openlocfilehash: 0d2a02ba9d89ba16e776bb73563eaebf8a92f1fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174904"
---
# <a name="qualifierset_delete-function"></a>QualifierSet_Delete funkcja
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
[w] Ten parametr jest nieużywane.

`ptr`[w] Wskaźnik do [wystąpienia IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)

`wszName`[w] Nazwa kwalifikatora do usunięcia.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr `wszName` jest nieprawidłowy. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | Usunięcie tego kwalifikatora jest niezgodne z prawem. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nie znaleziono określonego kwalifikatora. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | Lokalne zastąpienie zostało usunięte, a oryginalny kwalifikator z obiektu nadrzędnego został wznowiony zakres. |

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [metody IWbemQualifierSet::Delete.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete)

Ze względu na reguły propagacji kwalifikatora określonego kwalifikatora mogły być dziedziczone z innego obiektu i jedynie zastąpione w bieżącej klasie lub wystąpieniu. W takim przypadku `QualifierSet_Delete` metoda resetuje kwalifikator do oryginalnej wartości dziedziczonej. Funkcja w tym przypadku zwraca `WBEM_S_RESET_TO_DEFAULT`kod stanu .

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
