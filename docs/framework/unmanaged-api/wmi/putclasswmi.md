---
title: "Funkcja PutClassWmi (niezarządzany wykaz interfejsów API)"
description: "Funkcja PutClassWmi tworzy nową klasę lub aktualizuje istniejący zestaw."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutClassWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutClassWmi
helpviewer_keywords: PutClassWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 219cec2096cd3d1dfe1e0d3c0903b62692e444e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="putclasswmi-function"></a>Funkcja PutClassWmi
Tworzy nową klasę lub aktualizuje istniejący zestaw.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a>Parametry

`pObject`    
[in] Wskaźnik do prawidłową definicją klasy. Go muszą zostać poprawnie zainicjowane ze wszystkich wartości właściwości wymaganych.

`lFlags`   
[in] Kombinacja flag, które wpływają na działanie tej funkcji. Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie: 

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Jeśli zestaw, WMI nie przechowuje żadnych kwalifikatorów ze zmianami podtyp. </br> Jeśli nie zestawu, zakłada się, że ten obiekt nie jest lokalizowany, a wszystkie kwalifikatory są storedwith tego wystąpienia. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Jeśli nie istnieje lub jego zastąpienie, jeśli już istnieje, należy utworzyć klasę. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Aktualizacja klasy. Klasa musi istnieć wywołanie powiódł się. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Tworzenie klasy. Połączenie nie powiedzie się, jeśli klasa już istnieje. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje Półsynchroniczne wywołania. |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | Wypychania dostawcy należy określić tę flagę podczas wywoływania metody `PutClassWmi` aby wskazać, że ta klasa została zmieniona. |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | Umożliwia klasy aktualizacji, jeśli istnieją żadne klasy pochodnej i żadnych wystąpień tej klasy. Umożliwia także aktualizacje we wszystkich przypadkach, jeśli zmiana dotyczy tylko kwalifikatory bez znaczenia, takie jak kwalifikator opisu. Jeśli są wystąpienia klasy lub zmiany są ważne kwalifikatory, aktualizacja nie powiedzie się. |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | Umożliwia aktualizowanie klas, nawet jeśli są klasy podrzędne tak długo, jak zmiana nie powoduje konfliktów z klasy podrzędnej. Ta flaga umożliwia na przykład nową właściwość ma zostać dodana do klasy podstawowej, który nie został wcześniej wymienione w żadnej z klas podrzędnych. Jeśli są wystąpienia klasy aktualizacji nie powiedzie się. |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | Wymusza aktualizacje klas, gdy klasy podrzędne powodujące konflikt. Na przykład ta flaga wymusza aktualizację, jeśli kwalifikator klasa jest zdefiniowana w klasie podrzędnej, a klasa podstawowa próbuje dodać ten sam kwalifikator, który powoduje konflikt z jedną istniejących danych. W trybie wymuszania tis konflikt został rozwiązany przez usunięcie powodujące konflikt kwalifikator klasy podrzędnej. |

`pCtx`  
[in] Ta wartość jest zazwyczaj `null`. W przeciwnym razie jest wskaźnik do [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy. 

`ppCallResult`  
[out] Jeśli `null`, ten parametr nie jest używana. Jeśli `lFlags` zawiera `WBEM_FLAG_RETURN_IMMEDIATELY`, funkcja zwraca bezpośrednio z `WBEM_S_NO_ERROR`. `ppCallResult` Parametru otrzymuje wskaźnik do nowego [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) obiektu.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Użytkownik nie ma uprawnień do tworzenia lub modyfikowania klasy. |
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Określona klasa jest nieprawidłowa. Oznacza to, że zwykle `pObject` określa wystąpienie obiektu. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | Nazwa określona klasa jest nieprawidłowa. |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | Podjęto próbę dokonania zmiany, która będzie unieważnia podklasę. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` Określono flagę, ale klasa już istnieje. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`został określony w `lFlags`, a nie znaleziono klasy. |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | Wymagane właściwości dla klasy nie zostały ustawione. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do wykonania operacji. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Usługa WMI jest prawdopodobnie zatrzymana i ponownie uruchomić. Wywołanie [ConnectServerWmi](connectserverwmi.md) ponownie. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Procedury zdalnej łącze wywołań (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx) metody.

Użytkownik nie może utworzyć klasy o nazwach zaczynać się ani kończyć chacater podkreślenia

Jeśli wystąpi błąd wywołania funkcji, można uzyskać dodatkowe informacje o błędzie przez wywołanie metody [GetErrorInfo](geterrorinfo.md) funkcji.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
