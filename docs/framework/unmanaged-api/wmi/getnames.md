---
title: GetNames — funkcja (niezarządzana dokumentacja interfejsu API)
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
ms.openlocfilehash: 748767596a8f4680a2d7b63cb0579acaed5f53f8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798513"
---
# <a name="getnames-function"></a>GetNames, funkcja
Pobiera podzestaw lub wszystkie nazwy właściwości obiektu. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```cpp  
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
podczas Ten parametr jest nieużywany.

`ptr`  
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszQualifierName`  
podczas Wskaźnik do prawidłowego `LPCWSTR` , który określa nazwę kwalifikatora, który działa jako część filtra. Aby uzyskać więcej informacji, zobacz sekcję [uwagi](#remarks) . Ten parametr może być `null`. 

`lFlags`  
podczas Kombinacja pól bitowych. Aby uzyskać więcej informacji, zobacz sekcję [uwagi](#remarks) .

`pQualifierValue`   
podczas Zainicjowano wskaźnik do `VARIANT` prawidłowej struktury na wartość filtru. Ten parametr może być `null`. 

`pstrNames`  
określoną `SAFEARRAY` Struktura, która zawiera nazwy właściwości. We wpisie, ten parametr musi być zawsze wskaźnikiem `null`do. Zobacz sekcję [uwagi](#remarks) , aby uzyskać więcej informacji. 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Co najmniej jeden parametr jest nieprawidłowy lub określono niepoprawną kombinację flag i parametrów. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby ukończyć tę operację. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) .

Nazwane zwracane są kontrolowane przez kombinację flag i parametrów. Na przykład funkcja może zwracać nazwy wszystkich właściwości lub tylko nazwy właściwości klucza.  Filtr podstawowy jest określony w `lFlags` parametrze, a inne parametry różnią się w zależności od tego.

Wartości flag w programie `lFlags` są polami bitowymi

Flagi, które mogą być przesyłane jako `lEnumFlags` argument są polami bitowymi, które są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie.  Można połączyć jedną flagę z każdej grupy z dowolną flagą z dowolnej innej grupy. Jednak flagi z tej samej grupy wykluczają się wzajemnie. 

| Flagi grupy 1 |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Zwróć wszystkie nazwy właściwości. `strQualifierName`i `pQualifierVal` nie są używane. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Zwraca tylko właściwości, które mają kwalifikator o nazwie określonej przez `strQualifierName` parametr. Jeśli ta flaga jest używana, należy określić `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Zwraca tylko właściwości, które nie mają kwalifikatora nazwy określonej przez `strQualifierName` parametr. Jeśli ta flaga jest używana, należy określić `strQualifierName`. |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Zwróć tylko właściwości, które mają kwalifikator o nazwie określonej przez `wszQualifierName` parametr, a także mają wartość identyczną z określoną `pQualifierVal` przez strukturę. Jeśli ta flaga jest używana, należy określić zarówno `wszQualifierName` , `pQualifierValue`jak i. |

| Flagi grupy 2 |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Zwróć tylko nazwy właściwości, które definiują klucze. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Zwraca tylko nazwy właściwości, które są odwołaniami do obiektów. |

| Flagi grupy 3 |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Zwracaj tylko nazwy właściwości, które należą do klasy najbardziej pochodnej. Wyklucz właściwości z klas nadrzędnych. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Zwraca tylko nazwy właściwości należące do klas nadrzędnych. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Zwraca tylko nazwy właściwości systemu. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Zwróć tylko nazwy właściwości niesystemowych. |

Funkcja zawsze przydziela nowe `SAFEARRAY` , jeśli zwraca `WBEM_S_NO_ERROR`, i `pstrNames` zawsze jest ustawione na wartość. Zwracana tablica może zawierać 0 elementów, jeśli żadne właściwości nie pasują do określonych filtrów. Jeśli funkcja zwraca wartość inną niż `WBM_S_NO_ERROR`, Nowa `SAFEARRAY` struktura nie jest zwracana.
 
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** WMINet_Utils.idl  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
