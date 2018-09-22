---
title: Funkcja PutClassWmi (niezarządzany wykaz interfejsów API)
description: Funkcja PutClassWmi tworzy nową klasę lub aktualizuje istniejący zestaw.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de08662a825a84f19a40863cf73481d89364ebd0
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46568092"
---
# <a name="putclasswmi-function"></a>PutClassWmi — funkcja
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
[in] Wskaźnik do prawidłową definicją klasy. Jego musi być prawidłowo zainicjowany przy użyciu wartości wymaganej właściwości.

`lFlags`   
[in] Kombinacja flag, które mają wpływ na zachowanie tej funkcji. Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie: 

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Jeśli zestaw, usługa WMI nie przechowuje żadnych kwalifikatorów zmienionych wersji. </br> W przeciwnym razie zestawu, zakłada się, że ten obiekt nie jest zlokalizowana, a wszystkie kwalifikatory są storedwith tego wystąpienia. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Jeśli nie istnieje, lub go zastąpić, jeśli już istnieje, należy utworzyć klasę. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Aktualizacja klasy. Klasa musi istnieć przez wywołanie zakończy się powodzeniem. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Utwórz klasę. Wywołanie zakończy się niepowodzeniem, jeśli klasa już istnieje. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje, że wywołanie półsynchronicznej. |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | Dostawców wypychania należy określić tę flagę podczas wywoływania `PutClassWmi` do wskazania, że ta klasa została zmieniona. |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | Umożliwia klasy do zaktualizowania, jeśli istnieją nie klasy pochodne oraz żadnych wystąpień tej klasy. Umożliwia także aktualizacje we wszystkich przypadkach, jeśli ta zmiana jest tylko do "nieważne" kwalifikatorów, takich jak kwalifikator opisu. Jeśli są wystąpienia klasy lub zmiany mają ważne kwalifikatorów, aktualizacja nie powiedzie się. |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | Umożliwia aktualizowanie klas, nawet jeśli występują podrzędnego klasy tak długo, jak zmiany nie powoduje konfliktów z klasy podrzędne. Ta flaga umożliwia na przykład nową właściwość do dodania do klasy bazowej, która nie została wcześniej wymienione w dowolnej klasy podrzędne. Jeśli klasa ma wystąpień, aktualizacja nie powiedzie się. |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | Wymusza aktualizowanie klas, gdy klasy podrzędne powodujące konflikt. Na przykład ta flaga wymusza aktualizację, jeśli kwalifikator klasa jest zdefiniowana w klasie podrzędnej, a klasa bazowa próbuje dodać ten sam kwalifikator, który powoduje konflikt z jedną istniejących danych. W trybie wymuszania tym konflikt został rozwiązany przez usunięcie powodujące konflikt kwalifikator klasy podrzędnej. |

`pCtx`  
[in] Ta wartość jest zazwyczaj `null`. W przeciwnym razie jest wskaźnikiem do [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy. 

`ppCallResult`  
[out] Jeśli `null`, ten parametr jest nieużywana. Jeśli `lFlags` zawiera `WBEM_FLAG_RETURN_IMMEDIATELY`, funkcja zwraca natychmiast za pomocą `WBEM_S_NO_ERROR`. `ppCallResult` Parametru otrzymuje wskaźnik do nowego [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) obiektu.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Użytkownik nie ma uprawnień do utworzenia lub zmodyfikowania klasy. |
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Określona klasa jest nieprawidłowa. Oznacza to, że zwykle `pObject` określa obiektu wystąpienia. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | Nazwa określona klasa jest nieprawidłowa. |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | Podjęto próbę dokonania zmiany, który będzie unieważnia podklasę. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` Określono flagę, ale klasa już istnieje. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` został określony w `lFlags`, i nie można odnaleźć klasy. |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | Wymagane właściwości dla klasy nie wszystkie zostały ustawione. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI został prawdopodobnie zatrzymane i ponowne uruchamianie. Wywołaj [ConnectServerWmi](connectserverwmi.md) ponownie. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Procedury zdalnej łącza wywołania (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) metody.

Użytkownik nie może utworzyć klasy z nazwami będącymi zaczynać się ani kończyć znakiem podkreślenia chacater

Jeśli wywołanie funkcji zakończy się niepowodzeniem, można uzyskać dodatkowe informacje o błędzie, wywołując [geterrorinfo —](geterrorinfo.md) funkcji.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
