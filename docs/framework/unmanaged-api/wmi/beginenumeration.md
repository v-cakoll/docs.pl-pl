---
title: Beingenumeration — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja Beingenumeration resetuje moduł wyliczający na początku wyliczenia
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
ms.openlocfilehash: 9e467234a45ae702a5b77a5f0fa8b75d4ff03c52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124130"
---
# <a name="beginenumeration-function"></a>BeingEnumeration, funkcja
Resetuje moduł wyliczający z powrotem do początku wyliczenia.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`\
podczas Ten parametr jest nieużywany.

`ptr`\
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lEnumFlags`\
podczas Bitowa kombinacja flag lub wartości opisanych w sekcji [uwagi](#remarks) , która kontroluje właściwości zawarte w wyliczeniu.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Kombinacja flag w `lEnumFlags` jest nieprawidłowa lub określono nieprawidłowy argument. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Drugie wywołanie `BeginEnumeration` zostało wykonane bez interwencji wywołującego do [`EndEnumeration`](endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby rozpocząć nowe Wyliczenie. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject:: beingenumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

Flagi, które mogą być przesyłane jako argument `lEnumFlags`, są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie.  Można połączyć jedną flagę z każdej grupy z dowolną flagą z dowolnej innej grupy. Jednak flagi z tej samej grupy wykluczają się wzajemnie. 

**Grupa 1**

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Uwzględnij właściwości, które stanowią tylko klucz. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Dołącz właściwości, które są tylko odwołaniami do obiektów. |

**Grupa 2**

Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Ogranicz wyliczanie wyłącznie do właściwości systemu. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Uwzględnij właściwości lokalne i propagowane, ale Wyklucz właściwości systemu z wyliczenia. |

Dla klas:

Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Ogranicz Wyliczenie do właściwości zastąpionych w definicji klasy. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Ogranicz Wyliczenie do właściwości, które zostały zastąpione w bieżącej definicji klasy, i nowe właściwości zdefiniowane w klasie. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | Maska (a nie flaga) do zastosowania względem wartości `lEnumFlags`, aby sprawdzić, czy ustawiono `WBEM_FLAG_CLASS_OVERRIDES_ONLY` lub `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES`. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Ogranicz Wyliczenie do właściwości, które są zdefiniowane lub modyfikowane w samej klasie. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Ogranicz Wyliczenie do właściwości, które są dziedziczone z klas bazowych. |

Dla wystąpień:

Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Ogranicz Wyliczenie do właściwości, które są zdefiniowane lub modyfikowane w samej klasie. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Ogranicz Wyliczenie do właściwości, które są dziedziczone z klas bazowych. |

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils. idl  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
