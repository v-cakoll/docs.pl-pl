---
title: Funkcja ExecQueryWmi (niezarządzany wykaz interfejsów API)
description: Funkcja ExecQueryWmi wykonuje zapytanie, aby pobrać obiekty.
ms.date: 11/06/2017
api_name:
- ExecQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecQueryWmi
helpviewer_keywords:
- ExecQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc22edf51cbd726b69dff3da2f0540b2c3864f2e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929629"
---
# <a name="execquerywmi-function"></a>Funkcja ExecQueryWmi
Wykonuje zapytanie, aby pobrać obiekty.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ExecQueryWmi (
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
[in] Ciąg z językiem prawidłowe zapytanie obsługiwane przez Windows Management. Musi to być "WQL" akronim języka WMI Query Language.

`strQuery`  
[in] Tekst zapytania. Ten parametr nie może być `null`.

`lFlags`   
[in] Kombinacja flag, które mają wpływ na zachowanie tej funkcji. Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie: 

| Stała | Wartość  | Opis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Jeśli zestaw, funkcja pobiera poprawionych kwalifikatorów, przechowywane w zlokalizowanych nazw ustawień regionalnych bieżącego połączenia. <br/> W przeciwnym razie zestawu, funkcja pobiera kwalifikatory przechowywanych w bezpośrednim przestrzeni nazw. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje, że wywołanie półsynchronicznej. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Funkcja zwraca tylko do przodu modułu wyliczającego. Zwykle tylko do przodu moduły wyliczające są realizowane szybciej i używać mniej pamięci niż moduły wyliczające konwencjonalnych, ale nie zezwalają na wywołania [klonowania](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI zachowuje wskaźników do obiektów w enumration, dopóki ich wydaniu. | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | Zapewnia dowolnej zwracane obiekty mają wystarczającą ilość informacji w nich tak tej właściwości systemu, takie jak **__PATH**, **pobieranie właściwości __RELPATH**, i **__SERVER**, nie są `null`. |
| `WBEM_FLAG_PROTOTYPE` | 2 | Ta flaga jest używana do tworzenia prototypów. Go nie jest wykonywane zapytanie, a zamiast tego zwraca obiekt, który wygląda jak obiekt wyniku typowe. |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | Powoduje, że bezpośredni dostęp do dostawcy dla klasy określona bez względu na swoją klasą nadrzędną lub podklasy. |

Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` uzyskać najlepszą wydajność.

`pCtx`  
[in] Ta wartość jest zazwyczaj `null`. W przeciwnym razie jest wskaźnikiem do [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy. 

`ppEnum`  
[out] Jeśli żaden błąd nie wystąpi, otrzymuje wskaźnik, aby moduł wyliczający, który umożliwia obiektowi wywołującemu, można pobrać wystąpień w zestawie wyników zapytania. Zapytanie może mieć zestaw wyników z zerową wystąpień. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

`authLevel`  
[in] Poziom autoryzacji.

`impLevel` [in] Poziom personifikacji.

`pCurrentNamespace`   
[in] Wskaźnik do [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) obiekt, który reprezentuje bieżącej przestrzeni nazw.

`strUser`   
[in] Nazwa użytkownika. Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.

`strPassword`   
[in] Hasło. Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.

`strAuthority`   
[in] Nazwa domeny użytkownika. Zobacz [ConnectServerWmi](connectserverwmi.md) funkcji, aby uzyskać więcej informacji.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | Użytkownik nie ma uprawnień do wyświetlania przynajmniej jednej z klas, które może zwracać funkcji. |
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił nieokreślony błąd. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Zapytania ma błąd składni. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Żądany język kwerendy nie jest obsługiwane. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Zapytanie jest zbyt złożony. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI został prawdopodobnie zatrzymane i ponowne uruchamianie. Wywołaj [ConnectServerWmi](connectserverwmi.md) ponownie. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Procedury zdalnej łącza wywołania (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Zapytanie Określa klasę, która nie istnieje. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemServices::ExecQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execquery) metody.

Ta funkcja przetwarza zapytanie określone w `strQuery` parametru i tworzy moduł wyliczający, przez który obiekt wywołujący mogą uzyskiwać dostęp do wyników zapytania. Moduł wyliczający jest wskaźnikiem do [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) interfejsu; zapytanie wyniki są wystąpieniami typów obiektów klas udostępniane za pośrednictwem [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) interfejsu.

Istnieją limity liczby `AND` i `OR` słów kluczowych, które mogą być używane w kwerendach WQL. Dużej liczby WQL słowa kluczowe używane w złożonych kwerend może spowodować, że usługi WMI do zwrócenia `WBEM_E_QUOTA_VIOLATION` (lub 0x8004106c) kod błędu, jako `HRESULT` wartość. Limit słowa kluczowe języka WQL zależy od tego, jak złożona jest zapytanie.

Jeśli wywołanie funkcji zakończy się niepowodzeniem, można uzyskać dodatkowe informacje o błędzie, wywołując [geterrorinfo —](geterrorinfo.md) funkcji.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
