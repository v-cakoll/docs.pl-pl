---
title: "Usuwanie funkcji (niezarządzany wykaz interfejsów API)"
description: "Funkcja usuwania usuwa określonej właściwości i wszystkie jego kwalifikatory z definicji klasy modelu wspólnych informacji."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Delete
helpviewer_keywords: Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f32487d2bd59bd76acdc32218c6bb0842de20e87
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="delete-function"></a>Usuń — funkcja
Usuwa określonej właściwości i wszystkie jego kwalifikatory z definicji klasy modelu wspólnych informacji.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.

`wszName`  
[in] Nazwa właściwości do usunięcia. `wszName`musi być wskaźnikiem do prawidłowej `LPCWSTR`.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Nie można usunąć właściwości. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszzName` jest nieprawidłowy. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Określona właściwość nie istnieje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci do ukończenia tej operacji. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | Właściwość jest dziedziczona z klasy podstawowej. |
| `WBEM_E_SYSTEM_PROPERTY` | | Właściwość jest właściwością systemu. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | Funkcja usunąć zastąpienie wartości domyślne dla bieżącej klasy. Wartość domyślna tej właściwości w klasie nadrzędnej została reactiviated. | 

## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
