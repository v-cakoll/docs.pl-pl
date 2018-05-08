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
ms.openlocfilehash: 0db08ef4938a88ee657e2d65dda70edac09df8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="putinstancewmi-function"></a>Funkcja PutInstanceWmi
Tworzy lub aktualizuje wystąpienia istniejącej klasy. Wystąpienie jest zapisywany w repozytorium WMI. 

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
[in] Wskaźnik do wystąpienie było writen.

`lFlags`   
[in] Kombinacja flag, które wpływają na działanie tej funkcji. Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie: 

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Jeśli ustawiona, usługi WMI nie przechowuje żadnych kwalifikatorów z **zmieniony** podtyp. </br> Jeśli nie zestawu, zakłada się, że ten obiekt nie jest lokalizowany, a wszystkie kwalifikatory są storedwith tego wystąpienia. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Utworzenie wystąpienia, jeśli nie istnieje lub jego zastąpienie, jeśli już istnieje. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Zaktualizuj wystąpienie. Wystąpienie musi istnieć wywołanie powiódł się. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Utworzenie wystąpienia. Wywołanie zakończy się niepowodzeniem, jeśli wystąpienie już istnieje. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje Półsynchroniczne wywołania. |

`pCtx`  
[in] Ta wartość jest zazwyczaj `null`. W przeciwnym razie jest wskaźnik do [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy. 

`ppCallResult`  
[out] Jeśli `null`, ten parametr nie jest używana. Jeśli `lFlags` zawiera `WBEM_FLAG_RETURN_IMMEDIATELY`, funkcja zwraca bezpośrednio z `WBEM_S_NO_ERROR`. `ppCallResult` Parametru otrzymuje wskaźnik do nowego [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) obiektu.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Użytkownik nie ma uprawnień do zaktualizowania wystąpienia określonej klasy. |
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Klasy obsługi tego wystąpienia jest nieprawidłowa. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | `null` został określony dla właściwości, która nie może być `null`, takiej jak zostało oznaczone przez **indeksowane** lub **Not_Null** kwalifikatora. |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | Określone wystąpienie jest nieprawidłowy. (Na przykład wywołanie elementu `PutInstanceWmi` z klasą zwraca tę wartość.) |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY` Określono flagę, ale wystąpienie już istnieje. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` został określony w `lFlags`, ale wystąpienie nie istnieje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do wykonania operacji. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Usługa WMI jest prawdopodobnie zatrzymana i ponownie uruchomić. Wywołanie [ConnectServerWmi](connectserverwmi.md) ponownie. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Procedury zdalnej łącze wywołań (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) metody.

`PutInstanceWmi` Funkcji obsługuje tworzenie wystąpień i aktualizowanie wystąpień tylko istniejącej klasy.  W zależności od sposobu `pCtx` parametru jest ustawiona, niektórych lub wszystkich właściwości wystąpienia zostały zaktualizowane. 

Jeśli wystąpienie wskazywana przez `pInst` należy do podklasy, zarządzanie systemem Windows wywołania wszystkich dostawców odpowiedzialny za klasy, z których pochodzi podklasy. Wszystkie z tych dostawców musi niepowodzeniem dla oryginalnej `PutInstanceWmi` żądanie powiodło się. Dostawca obsługi klasie najwyższego poziomu w hierarchii jest nazywany najpierw. Kolejności wywoływania kontynuuje podklasa klasy najwyższego poziomu i będzie kontynuowane od góry do dołu, dopóki nie osiągnie zarządzania systemu Windows dostawcę dla klasy będącej właścicielem, jeśli wystąpienie wskazywana przez `pInst`.
Zarządzanie systemem Windows nie wywołuje dostawców dla każdego wystąpienia klasy podrzędnej. 

W przypadku aplikacji, należy zaktualizować wystąpienie, które należy do hierarchii klas, `pInst` parametru musi wskazywać wystąpienie zawierającego właściwości, które mają być modyfikowane. Oznacza to, należy wziąć pod uwagę obiektu docelowego, który należy do **ClassB**. **ClassB** wystąpienia jest pochodną **ClassA**, i **ClassA** definiuje właściwość **PropA**. Jeśli aplikacja chce wprowadzić zmianę do wartości **PropA** w **ClassB** wystąpienia, należy ustawić `pInst` do tego wystąpienia, a nie wystąpienia **ClassA** .

Wywoływanie `PutInstanceWmi` nie jest dozwolona w wystąpieniu klasy abstrakcyjnej.

Jeśli wystąpi błąd wywołania funkcji, można uzyskać dodatkowe informacje o błędzie przez wywołanie metody [GetErrorInfo](geterrorinfo.md) funkcji.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
