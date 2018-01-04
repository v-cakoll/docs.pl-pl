---
title: "Funkcja Beingenumeration (niezarządzany wykaz interfejsów API)"
description: "Funkcja Beingenumeration resetuje moduł wyliczający na początku wyliczenia"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BeginEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BeginEnumeration
helpviewer_keywords: BeginEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90c3e8448a61145290ea4a75b1d38f7ae010cb9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="beginenumeration-function"></a>Funkcja Beingenumeration
Moduł wyliczający resetuje do początku wyliczenia.  

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
[in] Ten parametr nie jest używana.

`ptr`[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.

`lEnumFlags`  
[in] Bitowe połączenie flagi lub wartości opisanych w [uwagi](#remarks) sekcji, która kontroluje właściwości zawarte w wyliczeniu.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Kombinacja flag w `lEnumFlags` jest nieprawidłowy lub nieprawidłowy argument został określony. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Drugie wywołanie `BeginEnumeration` został utworzony bez wywołania pośredniczące [ `EndEnumeration` ](endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Można rozpocząć nowego wyliczenia jest za mało pamięci. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) metody.

Flagi, które mogą być przekazywane jako `lEnumFlags` argumentu są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie.  Możesz łączyć jedną flagę z każdej grupy z flagą dowolnego z innej grupy. Jednak flagi z tej samej grupy wzajemnie się wykluczają. 

**Grupa 1**

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | Zawierają właściwości, które tworzą tylko klucz. |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | Zawierają właściwości, które są tylko odwołania do obiektów. |

**Grupa 2**

Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | Ogranicz wyliczenie tylko właściwości systemu. |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | Dołącz lokalnych i propagowany właściwości, z wyłączeniem właściwości systemu z wyliczenia. |

Dla klas:

Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | Ogranicz wyliczenia właściwości zastąpione w definicji klasy. |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | Ogranicz wyliczenia właściwości zastąpione w bieżącej definicji klas i nowe właściwości zdefiniowane w klasie. |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | A zamaskować (zamiast flagę) do zastosowania wobec `lEnumFlags` wartość, aby sprawdzić, czy albo `WBEM_FLAG_CLASS_OVERRIDES_ONLY` lub `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` jest ustawiona. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Ogranicz wyliczenia właściwości, które są zdefiniowane lub zmodyfikowany w samej klasy. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Ogranicz wyliczenia właściwości, które są dziedziczone z klas podstawowych. |

Dla wystąpień:

Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Ogranicz wyliczenia właściwości, które są zdefiniowane lub zmodyfikowany w samej klasy. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Ogranicz wyliczenia właściwości, które są dziedziczone z klas podstawowych. |


## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
