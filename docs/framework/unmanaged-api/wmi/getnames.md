---
title: GetNames, funkcja (odwołanie do niezarządzanego interfejsu API)
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
ms.openlocfilehash: 449f0ce9c291d4bbcad4947214e56ff46f55beed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174956"
---
# <a name="getnames-function"></a>GetNames, funkcja
Pobiera podzbiór lub wszystkie nazwy właściwości obiektu.

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
[w] Ten parametr jest nieużywane.

`ptr`  
[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszQualifierName`  
[w] Wskaźnik do prawidłowego, `LPCWSTR` który określa nazwę kwalifikatora, który działa jako część filtru. Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji. Ten parametr `null`może być .

`lFlags`  
[w] Kombinacja pól bitowych. Aby uzyskać więcej informacji, zobacz [uwagi](#remarks) sekcji.

`pQualifierValue`[w] Wskaźnik do prawidłowej `VARIANT` struktury zainicjowany do wartości filtru. Ten parametr `null`może być .

`pstrNames`  
[na zewnątrz] Struktura `SAFEARRAY` zawierająca nazwy właściwości. Przy wprowadzaniu ten parametr musi `null`być zawsze wskaźnikiem do . Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpiła ogólna porażka. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden lub więcej parametrów jest nieprawidłowych lub określono niepoprawną kombinację flag i parametrów. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do ukończenia operacji. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [metody IWbemClassObject::GetNames.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames)

Zwracane nazwy są kontrolowane przez kombinację flag i parametrów. Na przykład funkcja może zwracać nazwy wszystkich właściwości lub tylko nazwy właściwości klucza.  Filtr podstawowy jest określony `lFlags` w parametrze, a inne parametry różnią się w zależności od niego.

Wartości flagi `lFlags` są polami bitowymi

Flagi, które mogą być `lEnumFlags` przekazywane jako argument są pola bitowe, które są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie.  Można połączyć jedną flagę z każdej grupy z dowolną flagą z dowolnej innej grupy. Jednak flagi z tej samej grupy wzajemnie się wykluczają.

| Flagi grupy 1 |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | Zwraca wszystkie nazwy właściwości. `strQualifierName`i `pQualifierVal` są nieużywane. |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | Zwraca tylko właściwości, które mają kwalifikator nazwy określonej `strQualifierName` przez parametr. Jeśli ta flaga jest `strQualifierName`używana, należy określić . |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  Zwraca tylko właściwości, które nie mają kwalifikator nazwy określonej przez `strQualifierName` parametr. Jeśli ta flaga jest `strQualifierName`używana, należy określić . |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | Zwraca tylko właściwości, które mają kwalifikator nazwy określonej przez `wszQualifierName` parametr, `pQualifierVal` a także mają wartość identyczną z określoną przez strukturę. Jeśli ta flaga jest używana, `wszQualifierName` należy `pQualifierValue`określić zarówno a, jak i . |

| Flagi grupy 2 |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Zwraca tylko nazwy właściwości, które definiują klucze. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Zwracanie tylko nazw właściwości, które są odwołaniami do obiektów. |

| Flagi grupy 3 |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Zwraca tylko nazwy właściwości, które należą do najbardziej pochodnej klasy. Wyklucz właściwości z klas nadrzędnych. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Zwracanie tylko nazw właściwości, które należą do klas nadrzędnych. |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Zwraca tylko nazwy właściwości systemu. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Zwraca tylko nazwy właściwości niesystemowych. |

Funkcja zawsze przydziela nowy, `SAFEARRAY` jeśli `WBEM_S_NO_ERROR`zwraca `pstrNames` , i jest zawsze ustawiony, aby wskazać na niego. Zwrócona tablica może mieć 0 elementów, jeśli żadne właściwości nie pasują do określonych filtrów. Jeśli funkcja zwraca wartość `WBM_S_NO_ERROR`inną niż `SAFEARRAY` , nowa struktura nie jest zwracana.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
