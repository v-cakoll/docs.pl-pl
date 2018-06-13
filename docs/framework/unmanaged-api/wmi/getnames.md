---
title: GetNames — funkcja (niezarządzany wykaz interfejsów API)
description: Funkcja GetNames pobiera nazwy właściwości obiektu.
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 108946428cdfadcfb9c653b7e444bf278dfa2782
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461984"
---
# <a name="getnames-function"></a>GetNames — funkcja
Pobiera podzbiór lub wszystkie nazwy właściwości obiektu. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.

`wszQualifierName`  
[in] Wskaźnik do prawidłowej `LPCWSTR` określający nazwę kwalifikator, który działa jako część filtru. Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji. Ten parametr może być `null`. 

`lFlags`  
[in] Kombinacja pól bitowych. Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji.

`pQualifierValue`   
[in] Wskaźnik do prawidłowej `VARIANT` struktury zainicjowany do wartości filtru. Ten parametr może być `null`. 

`pstrNames`  
[out] A `SAFEARRAY` struktury, która zawiera nazwy właściwości. Na pozycji tego parametru zawsze musi być wskaźnikiem do `null`. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden lub więcej parametrów nie są prawidłowe, lub określono niepoprawne kombinacją flag i parametry. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do wykonania operacji. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::GetNames](https://msdn.microsoft.com/library/aa391447(v=vs.85).aspx) metody.

Nazwane zwracane są kontrolowane przez kombinacją flag i parametry. Na przykład funkcja może zwracać wszystkie właściwości lub tylko nazwy właściwości klucza.  Filtr główny jest określona w `lFlags` parametr i inne parametry różnią się w zależności od jej.

Wartości flagi `lFlags` są pola bitowe


Flagi, które mogą być przekazywane jako `lEnumFlags` argumentu są pola bitowe, które są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie.  Możesz łączyć jedną flagę z każdej grupy z flagą dowolnego z innej grupy. Jednak flagi z tej samej grupy wzajemnie się wykluczają. 

| Flagi grupy 1 |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Zwróć wszystkie nazwy właściwości. `strQualifierName` i `pQualifierVal` są używane. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Zwróć tylko właściwości, które mają Kwalifikator nazwy podanej przez `strQualifierName` parametru. Jeśli ta flaga jest wykorzystywana, należy określić `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Zwróć tylko właściwości, które nie mają Kwalifikator nazwy podanej przez `strQualifierName` parametru. Jeśli ta flaga jest wykorzystywana, należy określić `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Zwraca tylko te właściwości, które mają Kwalifikator nazwy podanej przez `wszQualifierName` parametr i wartość jest taka sama jak określona przez `pQualifierVal` struktury. Jeśli ta flaga jest wykorzystywana, należy określić zarówno `wszQualifierName` i `pQualifierValue`. |

| Flagi grupy 2 |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Zwraca tylko nazwy właściwości, które definiują kluczy. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Zwracane tylko nazwy właściwości, które są odwołania do obiektów. |

| Flagi grupa 3 |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Zwraca tylko te nazwy właściwości, które należą do klasy najdalszych pochodnych. Wyklucz właściwości z klasy nadrzędnej. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Zwraca tylko te nazwy właściwości, które należą do klasy nadrzędnej. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Zwraca tylko nazwy właściwości systemu. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Zwraca tylko nazwy właściwości nie ma systemu. |

Funkcja zawsze przydziela nowy `SAFEARRAY` Jeśli zwróci ona `WBEM_S_NO_ERROR`, i `pstrNames` ma zawsze wartość on. Zwracana tablica mogą mieć 0 elementów, jeśli nie znaleziono właściwości pasujących określonych filtrów. Jeśli funkcja zwraca wartość innych niż `WBM_S_NO_ERROR`, nowy `SAFEARRAY` struktury nie są zwracane.
 
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
