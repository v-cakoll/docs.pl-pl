---
title: Funkcja ExecNotificationQueryWmi (niezarządzany wykaz interfejsów API)
description: Funkcja ExecNotificationQueryWmi wykonuje zapytanie w celu odbierania zdarzeń.
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b5c26ab9c273b134915eea39078a83f569bcd32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462419"
---
# <a name="execnotificationquerywmi-function"></a>Funkcja ExecNotificationQueryWmi
Wykonuje zapytanie w celu odbierania zdarzeń. Wywołanie zwraca natychmiast, a obiekt wywołujący można sondować zwrócony modułu wyliczającego dla zdarzeń przychodzących. Zwalnianie zwrócony modułu wyliczającego anuluje zapytania.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ExecNotificationQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
); 
```  

## <a name="parameters"></a>Parametry

`strQueryLanguage`    
[in] Ciąg z prawidłowego zapytania języka obsługiwanego przez zarządzanie systemem Windows. Musi być "WQL" akronim język zapytań usługi WMI.

`strQuery`  
[in] Tekst zapytania. Ten parametr nie może być `null`.

`lFlags`   
[in] Kombinacja następujące dwie flagi, które wpływają na działanie tej funkcji. Te wartości są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie. 

| Stała | Wartość  | Opis  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje Półsynchroniczne wywołania. Jeśli ta flaga nie jest ustawiona, połączenie nie powiedzie się. Jest to spowodowane zdarzenia są odbierane w sposób ciągły, co oznacza, że użytkownik musi wykonać sondowanie zwrócony modułu wyliczającego. Blokuje to wywołanie w nieskończoność uniemożliwia który. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Funkcja zwraca tylko do przodu modułu wyliczającego. Zwykle tylko do przodu moduły wyliczające są szybsze i używają mniej pamięci niż wyliczenia z konwencjonalnej, ale nie zezwalają na wywołania [klonowania](clone.md). |

`pCtx`  
[in] Ta wartość jest zazwyczaj `null`. W przeciwnym razie jest wskaźnik do [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanych zdarzeń. 

`ppEnum`  
[out] Jeśli nie występują błędy, uzyskuje wskaźnik do moduł wyliczający, który umożliwia obiekt wywołujący, aby pobrać wystąpień w zestawie wyników kwerendy. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

`authLevel`  
[in] Poziom autoryzacji.

`impLevel` [in] Poziom personifikacji.

`pCurrentNamespace`   
[in] Wskaźnik do [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) obiekt, który reprezentuje bieżącej przestrzeni nazw.

`strUser`   
[in] Nazwa użytkownika. Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.

`strPassword`   
[in] Hasło. Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.

`strAuthority`   
[in] Nazwa domeny użytkownika. Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Użytkownik nie ma uprawnień do wyświetlania przynajmniej jednej z klas, które może zwracać funkcji. |
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | Kwerenda Określa klasę, która nie istnieje. |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | 0x80042002 | Zażądano zbyt dużo dokładność w dostarczania zdarzeń. Należy określić większą tolerancją sondowania. |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | 0x80042001 | Requess zapytań zapewniają więcej informacji niż zarządzanie systemem Windows. To `HRESULT` jest zwracany, gdy kwerenda powoduje żądanie, aby wykonać sondowanie wszystkie obiekty w przestrzeni nazw. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Zapytania wystąpił błąd składni. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Żądany język kwerendy nie jest obsługiwane. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Zapytanie jest zbyt złożony. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do wykonania operacji. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Usługa WMI jest prawdopodobnie zatrzymana i ponownie uruchomić. Wywołanie [ConnectServerWmi](connectserverwmi.md) ponownie. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Procedury zdalnej łącze wywołań (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_E_UNPARSABLE_QUERY` | 0x80041058 | Nie można przeanalizować zapytania. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemServices::ExecNotificationQuery](https://msdn.microsoft.com/library/aa392105(v=vs.85).aspx) metody.

Po powrocie z funkcji okresowo wywołujący zwróconego `ppEnum` do obiektu [dalej](next.md) funkcji, aby sprawdzić, czy wszystkie zdarzenia są dostępne.

Istnieją ograniczenia liczby `AND` i `OR` słów kluczowych, które mogą być używane w zapytaniach WQL. Dużą liczbą słów kluczowych języka WQL używanych w zapytaniu złożonych może spowodować WMI do zwrócenia `WBEM_E_QUOTA_VIOLATION` (lub 0x8004106c) kod błędu jako `HRESULT` wartość. Limit słów kluczowych języka WQL zależy od tego, jak złożoność zapytanie jest.

Jeśli wystąpi błąd wywołania funkcji, można uzyskać dodatkowe informacje o błędzie przez wywołanie metody [GetErrorInfo](geterrorinfo.md) funkcji.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
