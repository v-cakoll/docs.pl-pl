---
title: Funkcja GetNames (niezarządzany wykaz interfejsów API)
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
ms.openlocfilehash: b0065b2cbbd17c5bb3dca6773951cdb8729e59fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583564"
---
# <a name="getnames-function"></a>Funkcja GetNames
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
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`wszQualifierName`  
[in] Wskaźnik do prawidłowego `LPCWSTR` określający nazwę kwalifikator, która działa jako część filtru. Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji. Ten parametr może być `null`. 

`lFlags`  
[in] Kombinacja pól bitowych. Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji.

`pQualifierValue`   
[in] Wskaźnik do prawidłowego `VARIANT` struktury inicjowany do wartości filtru. Ten parametr może być `null`. 

`pstrNames`  
[out] A `SAFEARRAY` strukturę, która zawiera nazwy właściwości. Przy uruchamianiu, ten parametr musi być zawsze wskaźnik do `null`. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji. 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden lub więcej parametrów są nieprawidłowe lub została określona nieprawidłowa kombinacja flag i parametry. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) metody.

Nazwane zwracane są kontrolowane przez kombinacja flag i parametry. Na przykład funkcja może zwrócić wszystkie właściwości lub tylko nazwy właściwości klucza.  Filtr podstawowy jest określony w `lFlags` parametru i inne parametry różnią się w zależności od jego.

Flaga wartości w `lFlags` pól bitowych


Flagi, które mogą być przekazywane jako `lEnumFlags` należą pola bitowe, które są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie.  Można łączyć z jedną flagę z każdej grupy za pomocą jakakolwiek Flaga w żadnej innej grupy. Jednak flagi z tej samej grupy wzajemnie się wykluczają. 

| Flagi grupy 1 |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Zwróć wszystkie nazwy właściwości. `strQualifierName` i `pQualifierVal` są używane. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Zwraca tylko właściwości, które mają kwalifikator o nazwie określonej przez `strQualifierName` parametru. Jeśli ta flaga jest używany, należy określić `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Zwraca tylko właściwości, które nie mają kwalifikator o nazwie określonej przez `strQualifierName` parametru. Jeśli ta flaga jest używany, należy określić `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Zwraca tylko te właściwości, które mają kwalifikator o nazwie określonej przez `wszQualifierName` parametru i także mieć wartość taka sama jak określona przez `pQualifierVal` struktury. Jeśli ta flaga jest używany, należy określić zarówno `wszQualifierName` i `pQualifierValue`. |

| Flags — grupa 2 |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Zwraca tylko nazwy właściwości, które definiują kluczy. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Zwracane tylko nazwy właściwości, które są odwołania do obiektu. |

| Flagi grupa 3 |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Zwróć tylko nazwy właściwości, które należą do najbardziej pochodnej klasy. Wyklucz właściwości z klasy nadrzędnej. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Zwróć tylko nazwy właściwości, które należą do klasy nadrzędnej. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Zwraca tylko nazwy właściwości systemu. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Zwraca tylko nazwy właściwości-system. |

Funkcja zawsze przydziela nową `SAFEARRAY` Jeśli zwróci ona `WBEM_S_NO_ERROR`, i `pstrNames` ma zawsze wartość on. Zwracana tablica może mieć 0 elementów, jeśli nie znaleziono właściwości pasujących określonych filtrów. Jeśli funkcja zwraca wartości innych niż `WBM_S_NO_ERROR`, nowy `SAFEARRAY` struktura nie jest zwracana.
 
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
