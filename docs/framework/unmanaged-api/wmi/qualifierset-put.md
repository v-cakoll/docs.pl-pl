---
title: Funkcja QualifierSet_Put (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_Put zapisuje kwalifikator nazwanych i jego wartość.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e1fc8d9d8c135f9eea8b9451b884ef3b7ba4704
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694142"
---
# <a name="qualifiersetput-function"></a>QualifierSet_Put — funkcja
Zapisuje kwalifikator o nazwie i wartości. Nowy kwalifikator zastępuje poprzednią wartość taką samą nazwę. Jeśli kwalifikatora nie istnieje, zostanie utworzony. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`   
[in] Ten parametr jest nieużywany.

`ptr`   
[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.

`wszName`   
[in] Nazwa kwalifikatora do zapisania.

`pVal` [in] Wskaźnik do prawidłowego `VARIANT` zawierający kwalifikator do zapisania. Ten parametr nie może być `null`.

`lFlavor` [in] Jeden z następujących stałych, które definiuje właściwą kwalifikator odpowiednią dla tego kwalifikatora. Wartość domyślna to `WBEM_FLAVOR_OVERRIDABLE` (0).

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | Kwalifikator może zostać przesłonięta w pochodnej klasy lub wystąpienia. **Jest to wartość domyślna.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | Kwalifikator jest propagowana do wystąpienia. |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | Kwalifikator jest propagowana do klas pochodnych. |
| `WBEM_FLAVOR_NOT_OVERRIDABLE | 0x10 | Nie można zastąpić kwalifikator w klasie pochodnej lub wystąpienia. |
| "WBEM_FLAVOR_AMENDED | 0x80 | Kwalifikator jest zlokalizowana. |

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Wystąpił niedozwolona próba określenia **klucz** kwalifikator dla właściwości, która nie może być kluczem. Klucze są określone om c; definicji klasy dla obiektu i nie może zostać zmieniona na podstawie poszczególnych wystąpień. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal` Parametr nie jest dozwolonym typem kwalifikatora. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Nie jest możliwe do wywołania `QualifierSet_Put` metody kwalifikator, ponieważ obiekt-właściciel nie zezwala na zastąpienia. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
