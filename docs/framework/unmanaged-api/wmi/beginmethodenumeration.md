---
title: Funkcja BeginMethodEnumeration (niezarządzany wykaz interfejsów API)
description: Funkcja BeginMethodEnumeration, rozpoczyna się wyliczenie metod obiektu
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d6de2a5ff4d2743c7aca2e46b3af848138c15fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158785"
---
# <a name="beginenumeration-function"></a>BeingEnumeration, funkcja
Rozpoczyna się wyliczenie metody dostępne dla obiektu.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`lEnumFlags`  
[in] Zero (0) dla wszystkich metod lub flagę, która określa zakres wyliczenia. Następujące flagi są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Ograniczenie wyliczenia do metod, które są zdefiniowane w samej klasy. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Ograniczenie wyliczenia właściwości, które są dziedziczone z klasy bazowej. |

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lEnnumFlags` jest różna od zera i nie jest jedną z określonych flag. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) metody.

Wywołanie tej metody jest obsługiwana tylko w przypadku, jeśli bieżący obiekt jest definicją klasy. Metoda manipulowania nie jest dostępna z [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskaźniki prowadzące do wystąpienia. Kolejność, w którym są wyliczane metody może być inwariantny dla danego wystąpienia programu [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
