---
title: Funkcja Beingenumeration (niezarządzany wykaz interfejsów API)
description: Funkcja Beingenumeration resetuje moduł wyliczający na początku tego wyliczenia
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08406f7d93671b406b3c7cd8719a7a0e5e423184
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523505"
---
# <a name="beginenumeration-function"></a>Funkcja Beingenumeration
Resetuje modułu wyliczającego do początku wyliczenia.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr jest nieużywany.

`ptr` [in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`lEnumFlags`  
[in] Bitowa kombinacja wartości opisanych w lub flag [uwagi](#remarks) sekcji, która kontroluje właściwości zawartych w wyliczeniu.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Kombinacja flag w `lEnumFlags` jest nieprawidłowy lub nieprawidłowy argument został określony. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Drugie wywołanie `BeginEnumeration` został utworzony bez interwencyjnego wywołania [ `EndEnumeration` ](endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny rozpocząć nowe wyliczenie. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) metody.

Flagi, które mogą być przekazywane jako `lEnumFlags` argument są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie.  Można łączyć z jedną flagę z każdej grupy za pomocą jakakolwiek Flaga w żadnej innej grupy. Jednak flagi z tej samej grupy wzajemnie się wykluczają. 

**Grupa 1**

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Zawierają właściwości, które stanowią tylko klucz. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Zawierają właściwości, które są tylko odwołania do obiektu. |

**Grupa 2**

Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Ograniczenie wyliczenia tylko właściwości systemu. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Dołącz właściwości lokalne i propagowany, ale wykluczyć wyliczenia właściwości systemu. |

Dla klas:

Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Ograniczenie wyliczenia właściwości przesłonięcia w definicji klasy. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Ograniczenie wyliczenia właściwości zastąpione w bieżącej definicji klas i nowe właściwości zdefiniowane w klasie. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | A maski (zamiast flaga) do zastosowania wobec `lEnumFlags` wartość, aby sprawdzić, czy w obu `WBEM_FLAG_CLASS_OVERRIDES_ONLY` lub `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` jest ustawiona. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Ograniczenie wyliczenia właściwości, które są zdefiniowane lub zmodyfikowany w samej klasy. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Ograniczenie wyliczenia właściwości, które są dziedziczone z klasy bazowej. |

Dla wystąpień:

Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Ograniczenie wyliczenia właściwości, które są zdefiniowane lub zmodyfikowany w samej klasy. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Ograniczenie wyliczenia właściwości, które są dziedziczone z klasy bazowej. |


## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
