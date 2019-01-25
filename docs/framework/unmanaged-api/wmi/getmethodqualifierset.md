---
title: Funkcja GetMethodQualifierSet (niezarządzany wykaz interfejsów API)
description: Funkcja GetMethodQualifierSet pobiera zestaw kwalifikator metody.
ms.date: 11/06/2017
api_name:
- GetMethodQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodQualifierSet
helpviewer_keywords:
- GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f197851d4d7d470c6c34e4f5607e1791e724770
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681628"
---
# <a name="getmethodqualifierset-function"></a>Funkcja GetMethodQualifierSet
Pobiera kwalifikator ustawione dla konkretnych metod.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`wszMethod`  
[in] Nazwa metody. `wszMethod` musi wskazywać prawidłowy `LPCWSTR`. 

`ppQualSet`  
[out] Otrzymuje wskaźnik interfejsu, który umożliwia dostęp do kwalifikatory metody. `ppQualSet` nie może być `null`. Jeśli wystąpi błąd, nowy obiekt nie jest zwracana i wskaźnik jest ustawiony na wskaż `null`. 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Określona metoda nie istnieje. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest `null`. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) metody. 

Wywołanie tej funkcji jest obsługiwana tylko wtedy, gdy bieżący obiekt jest definicją klasy modelu wspólnych informacji. Metoda manipulowania nie jest dostępna dla [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters wskazujące wystąpienia modelu CIM.

Ponieważ każda metoda może mieć własną kwalifikatory [wskaźnik IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) umożliwia obiekt wywołujący, dodawać, edytować lub usuwać kwalifikatory.

## <a name="requirements"></a>Wymagania  
**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
