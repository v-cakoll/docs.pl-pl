---
title: BeginEnumeration, funkcja (odwołanie do niezarządzanego interfejsu API)
description: Funkcja BeginEnumeration resetuje wyliczenia do początku wyliczenia
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
ms.openlocfilehash: eac23916bd78ec3970a87566e2d2f4d79b379824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176880"
---
# <a name="beginenumeration-function"></a>BeingEnumeration, funkcja
Resetuje wyliczenia z powrotem do początku wyliczenia.  

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
[w] Ten parametr jest nieużywane.

`ptr`\
[w] Wskaźnik do wystąpienia [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`lEnumFlags`\
[w] Bitowe połączenie flag lub wartości [opisanych](#remarks) w uwagi sekcji, która kontroluje właściwości zawarte w wyliczeniu.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Kombinacja flag `lEnumFlags` jest nieprawidłowa lub określono nieprawidłowy argument. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Drugie wezwanie `BeginEnumeration` zostało wykonane bez interwencji [`EndEnumeration`](endenumeration.md)połączenia do . |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna, aby rozpocząć nowe wyliczenie. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie metody [IWbemClassObject::BeginEnumeration.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

Flagi, które mogą być `lEnumFlags` przekazywane jako argument są zdefiniowane w pliku nagłówka *WbemCli.h* lub można zdefiniować je jako stałe w kodzie.  Można połączyć jedną flagę z każdej grupy z dowolną flagą z dowolnej innej grupy. Jednak flagi z tej samej grupy wzajemnie się wykluczają.

**Grupa 1**

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Uwzględnij właściwości, które stanowią tylko klucz. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Uwzględnij właściwości, które są tylko odwołaniami do obiektów. |

**Grupa 2**

Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Ogranicz wyliczenie tylko do właściwości systemu. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Uwzględnij właściwości lokalne i propagowane, ale wyklucz właściwości systemu z wyliczenia. |

Dla klas:

Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Ogranicz wyliczenie do właściwości zastąpionych w definicji klasy. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Ogranicz wyliczenie do właściwości nadpisywać w bieżącej definicji klasy i do nowych właściwości zdefiniowanych w klasie. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | Maska (a nie flaga), `lEnumFlags` aby zastosować względem `WBEM_FLAG_CLASS_OVERRIDES_ONLY` wartości, aby sprawdzić, czy albo `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` jest ustawiona. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Ogranicz wyliczenie do właściwości, które są zdefiniowane lub zmodyfikowane w samej klasie. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Ogranicz wyliczenie do właściwości, które są dziedziczone z klas podstawowych. |

W przypadku:

Stały  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Ogranicz wyliczenie do właściwości, które są zdefiniowane lub zmodyfikowane w samej klasie. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Ogranicz wyliczenie do właściwości, które są dziedziczone z klas podstawowych. |

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
