---
title: "Funkcja GetPropertyQualifierSet (niezarządzany wykaz interfejsów API)"
description: "Funkcja GetPropertyQualifierSet pobiera kwalifikator, ustaw dla właściwości."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ca2981c8833abaafd5d206b66d6e91f34e2c91d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getpropertyqualifierset-function"></a>Funkcja GetPropertyQualifierSet
Pobiera kwalifikator ustawić dla określonej właściwości.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.

`wszMethod`  
[in] Nazwa właściwości. `wszProperty`musi wskazywać prawidłowe `LPCWSTR`. 

`ppQualSet`  
[out] Odbiera wskaźnika interfejsu, który zezwala na dostęp do kwalifikatory właściwości. `ppQualSet`nie może być `null`. Jeśli wystąpi błąd, nowego obiektu nie są zwracane, a wskaźnik ma ustawioną wartość wskaż `null`. 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Określona metoda nie istnieje. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do wykonania operacji. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest `null`. |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | Funkcja podejmie próbę uzyskania kwalifikatorów właściwości systemu. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) metody. 

Wywołanie tej funkcji jest obsługiwana tylko wtedy, gdy bieżący obiekt jest definicję klasy modelu wspólnych informacji. Metoda manipulowania nie jest dostępna dla [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters wskazujące wystąpienia modelu CIM.

Ponieważ każda metoda może mieć własną kwalifikatory [wskaźnika IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) umożliwia wywołującego dodać, edytować lub usunąć kwalifikatory.

Ponieważ właściwości systemu nie ma żadnych kwalifikatorów, funkcja zwraca `WBEM_E_SYSTEM_PROPERTY` przy próbie uzyskania [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) wskaźnika dla właściwości systemu.

## <a name="requirements"></a>Wymagania  
**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
