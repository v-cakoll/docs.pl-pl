---
title: Funkcja GetQualifierSet (niezarządzany wykaz interfejsów API)
description: Funkcja GetQualifierSet pobiera kwalifikator dla klasy lub wystąpienia.
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b50befa4346e17048598afd3d018dbde2fe8572
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458565"
---
# <a name="getqualifierset-function"></a>Funkcja GetQualifierSet
Pobiera kwalifikator dla wystąpienia klasy lub definicji klasy.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.

`ppQualSet`  
[out] Uzyskuje wskaźnik interfejsu, który zezwala na dostęp do kwalifikatory klasy obiektu. `ppQualSet` nie może być `null`. Jeśli wystąpi błąd, nowego obiektu nie są zwracane, a wskaźnik myszy pozostanie niezmieniona. 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Określona metoda nie istnieje. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do wykonania operacji. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest `null`. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::GetQualifierSet](https://msdn.microsoft.com/library/aa391451(v=vs.85).aspx) metody. 

[Wskaźnika IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) umożliwia wywołującego dodać, edytować lub usunąć kwalifikatory. Takie kwalifikatory dodany, edycji lub usunięty mają zastosowanie do całego wystąpienia lub definicję klasy.

## <a name="requirements"></a>Wymagania  
**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
