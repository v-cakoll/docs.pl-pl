---
title: Funkcja QualifierSet_Put (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_Put zapisuje kwalifikator nazwane i jej wartość.
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
ms.openlocfilehash: 7ccb0aef0e998ffccd7526f9f0554bceb892001b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="qualifiersetput-function"></a>Funkcja QualifierSet_Put
Zapisuje kwalifikator o nazwie i wartości. Nowy kwalifikator spowoduje zastąpienie poprzedniej wartości o takiej samej nazwie. Jeśli kwalifikator nie istnieje, jest tworzony. 

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
[in] Ten parametr nie jest używana.

`ptr`   
[in] Wskaźnik do [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) wystąpienia.

`wszName`   
[in] Nazwa kwalifikatora do zapisu.

`pVal` [in] Wskaźnik do prawidłowej `VARIANT` zawierający kwalifikator do zapisu. Ten parametr nie może być `null`.

`lFlavor` [in] Jeden z następujących stałych, które definiuje odmian kwalifikator odpowiednią dla tego kwalifikatora. Wartość domyślna to `WBEM_FLAVOR_OVERRIDABLE` (0).

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | Kwalifikator może zostać przesłonięta w pochodnej klasy lub wystąpienia. **Jest to wartość domyślna.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | Kwalifikator jest propagowana do wystąpień. |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | Kwalifikator jest propagowana do klas pochodnych. |
| "WBEM_FLAVOR_NOT_OVERRIDABLE | 0x10 | Nie można zastąpić kwalifikator w klasie pochodnej lub wystąpienia. |
| "WBEM_FLAVOR_AMENDED | 0x80 | Kwalifikator jest zlokalizowana. |

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Znaleziono niedozwolona próba określenia **klucza** kwalifikator dla właściwości, która nie może być kluczem. Klucze są określone om c; ści definicji dla obiektu i nie można ich zmieniać dla poszczególnych wystąpień. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal` Parametr nie jest dozwolonym typem kwalifikatora. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Nie jest możliwe do wywołania `QualifierSet_Put` metoda kwalifikator, ponieważ jego obiekt-właściciel nie zezwala na zastępowanie. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
