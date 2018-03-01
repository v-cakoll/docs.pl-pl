---
title: "Funkcja QualifierSet_BeginEnumeration (niezarządzany wykaz interfejsów API)"
description: "Funkcja QualifierSet_BeginEnumeration resetuje moduł wyliczający kwalifikatory obiektu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 440dde03f4ed138a33eb6f817723d7c5c74f6d46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetbeginenumeration-function"></a>Funkcja QualifierSet_BeginEnumeration
Resetuje moduł wyliczający kwalifikatory obiekt na początek wyliczenia.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`   
[in] Ten parametr nie jest używana.

`ptr`   
[in] Wskaźnik do [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) wystąpienia.

`lFlags`   
[in] Bitowe połączenie flagi lub wartości opisanych w [uwagi](#remarks) sekcja, która określa kwalifikatory do uwzględnienia w wyliczeniu.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags` Parametr jest nieprawidłowy. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Drugie wywołanie `QualifierSet_BeginEnumeration` został utworzony bez wywołania pośredniczące [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Można rozpocząć nowego wyliczenia jest za mało pamięci. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx) metody.

Aby wyliczyć wszystkie kwalifikatory dla obiekt, ta metoda musi zostać wywołana przed pierwsze wywołanie w celu [QualifierSet_Next](qualifierset-next.md). Kolejność, w którym są wyliczane kwalifikatory gwarantuje to niezmiennej danego wyliczenia.

Flagi, które mogą być przekazywane jako `lEnumFlags` argumentu są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie.   

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|  | 0 | Zwraca nazwy wszystkich kwalifikatorów. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Zwraca tylko nazwy kwalifikatory określonych bieżącą właściwość lub obiekt. <br/> Dla właściwości: zwracać tylko kwalifikatory określonego we właściwości (w tym zastąpień), a nie te kwalifikatory propagowane z definicji klasy. <br/> Dla wystąpienia obiektu: zwraca tylko nazwy kwalifikator danego wystąpienia. <br/> Dla klasy: przywrócenie tylko kwalifikatory określonych beiong klasy pochodnej.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Powrót propagowane tylko nazwy kwalifikatory z innego obiektu. <br/> Dla właściwości: zwracane tylko kwalifikatory propagowane do tej właściwości z definicji klasy, a nie te z samej właściwości. <br/> Dla wystąpienia obiektu: Powrót propagowane tylko tych kwalifikatory z definicji klasy. <br/> Dla klasy: zwracane tylko nazwy kwalifikator odziedziczona z klasy nadrzędnej. |

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
