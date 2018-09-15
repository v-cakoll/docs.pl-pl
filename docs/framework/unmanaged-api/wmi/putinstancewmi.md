---
title: Funkcja PutInstanceWmi (niezarządzany wykaz interfejsów API)
description: Funkcja PutInstanceWmi tworzy lub aktualizuje wystąpienia istniejącej klasy.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67abf017040b9e6bbe9b10e560c8d57c124ae84e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625285"
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi — funkcja
Tworzy lub aktualizuje wystąpienia istniejącej klasy. Wystąpienie jest zapisywany do repozytorium WMI. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a>Parametry

`pInst`    
[in] Wskaźnik do wystąpienia jako writen.

`lFlags`   
[in] Kombinacja flag, które mają wpływ na zachowanie tej funkcji. Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie: 

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Jeśli ustawiona, usługi WMI nie przechowuje żadnych kwalifikatorów z **zmieniony** wersja. </br> W przeciwnym razie zestawu, zakłada się, że ten obiekt nie jest zlokalizowana, a wszystkie kwalifikatory są storedwith tego wystąpienia. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Utwórz wystąpienie, jeśli on nie istnieje, lub go zastąpić, jeśli już istnieje. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Aktualizuj wystąpienia. Wystąpienie musi istnieć przez wywołanie zakończy się powodzeniem. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Utwórz wystąpienie. Wywołanie zakończy się niepowodzeniem, jeśli wystąpienie już istnieje. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje, że wywołanie półsynchronicznej. |

`pCtx`  
[in] Ta wartość jest zazwyczaj `null`. W przeciwnym razie jest wskaźnikiem do [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy. 

`ppCallResult`  
[out] Jeśli `null`, ten parametr jest nieużywana. Jeśli `lFlags` zawiera `WBEM_FLAG_RETURN_IMMEDIATELY`, funkcja zwraca natychmiast za pomocą `WBEM_S_NO_ERROR`. `ppCallResult` Parametru otrzymuje wskaźnik do nowego [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) obiektu.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Użytkownik nie ma uprawnień do aktualizowania wystąpienie określonej klasy. |
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Klasy obsługi tego wystąpienia jest nieprawidłowy. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | `null` została określona dla właściwości, która nie może być `null`, taki, który jest oznaczony za **indeksowany** lub **Not_Null** kwalifikator. |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | Określone wystąpienie jest nieprawidłowy. (Na przykład, wywołanie `PutInstanceWmi` za pomocą klasy zwraca tę wartość.) |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` Określono flagę, ale wystąpienie już istnieje. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` został określony w `lFlags`, ale wystąpienie nie istnieje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI został prawdopodobnie zatrzymane i ponowne uruchamianie. Wywołaj [ConnectServerWmi](connectserverwmi.md) ponownie. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Procedury zdalnej łącza wywołania (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) metody.

`PutInstanceWmi` Obsługuje tworzenie wystąpień i aktualizowanie wystąpień istniejące klasy tylko funkcji.  W zależności od sposobu `pCtx` zestaw parametrów, niektórych lub wszystkich właściwości wystąpienia są aktualizowane. 

Gdy wystąpienie wskazywany przez `pInst` należy do podklasy, Windows Management wywołania odpowiedzialny za klasy, z których pochodzi podklasy dostawców. Wszystkie z tych dostawców musi zakończyć się dla oryginalnej `PutInstanceWmi` żądanie zakończyło się sukcesem. Najpierw nosi nazwę dostawcy, obsługujące klasie najwyższego poziomu w hierarchii. Kolejności wywoływania będzie kontynuowane z użyciem podklasę klasy najwyższego poziomu i rozpoczynające się od góry do dołu dopóki nie osiągnie zarządzania Windows dostawca dla klasy będącej właścicielem wystąpienia wskazywany przez `pInst`.
Windows Management nie wywołuje dostawców dla każdego wystąpienia klasy podrzędne. 

Jeśli aplikacja musi zaktualizować wystąpienie, które należy do hierarchii klas, `pInst` parametru musi wskazywać na wystąpienie zawierającego właściwości, które mają być modyfikowane. Oznacza to, należy wziąć pod uwagę wystąpienie docelowe, który należy do **ClassB**. **ClassB** wystąpienia jest pochodną **ClassA**, i **ClassA** nie definiuje właściwości **PropA**. Jeśli aplikacja chce, aby wprowadzić zmiany do wartości **PropA** w **ClassB** wystąpienia, należy ustawić `pInst` tego wystąpienia, a nie wystąpieniem **ClassA** .

Wywoływanie `PutInstanceWmi` nie jest dozwolona w wystąpieniu klasy abstrakcyjnej.

Jeśli wywołanie funkcji zakończy się niepowodzeniem, można uzyskać dodatkowe informacje o błędzie, wywołując [geterrorinfo —](geterrorinfo.md) funkcji.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
