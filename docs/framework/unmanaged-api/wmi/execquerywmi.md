---
title: "Funkcja ExecQueryWmi (niezarządzany wykaz interfejsów API)"
description: "Funkcja ExecQueryWmi wykonuje zapytanie w celu pobrania obiektów."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ExecQueryWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ExecQueryWmi
helpviewer_keywords: ExecQueryWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 872109cb0472a8404c492c2867429fe783f898eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="execquerywmi-function"></a>Funkcja ExecQueryWmi
Wykonuje zapytanie w celu pobrania obiektów.  

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
[in] Ciąg z prawidłowego zapytania języka obsługiwanego przez zarządzanie systemem Windows. Musi być "WQL" akronim język zapytań usługi WMI.

`strQuery`  
[in] Tekst zapytania. Ten parametr nie może być `null`.

`lFlags`   
[in] Kombinacja flag, które wpływają na działanie tej funkcji. Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie: 

| Stała | Wartość  | Opis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Jeśli zestaw, funkcja pobiera poprawionych kwalifikatorów przechowywane w zlokalizowanych nazw ustawień regionalnych bieżącego połączenia. <br/> Jeśli nie zestawu, funkcja pobiera tylko kwalifikatory przechowywane w przestrzeni nazw bezpośrednim. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje Półsynchroniczne wywołania. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Funkcja zwraca tylko do przodu modułu wyliczającego. Zwykle tylko do przodu moduły wyliczające są szybsze i używają mniej pamięci niż wyliczenia z konwencjonalnej, ale nie zezwalają na wywołania [klonowania](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI zachowuje wskaźników do obiektów w enumration, dopóki ich wydania. | 
| `WBEM_FLAG_ENSURE_LOCATABLE` | 0x100 | Zapewnia żadnego zwracane obiekty mają wystarczającą ilość informacji w nich sposób tej właściwości systemu, takich jak **__PATH**, **pobieranie właściwości __RELPATH**, i **__SERVER**, nie są `null`. |
| `WBEM_FLAG_PROTOTYPE` | 2 | Ta flaga jest wykorzystywana do tworzenia prototypów. Nie wykonuj zapytania, a zamiast tego zwraca obiekt, który wygląda jak obiekt wyniku typowych. |
| `WBEM_FLAG_DIRECT_READ` | 0x200 | Przyczyny bezpośredni dostęp do dostawcy dla klasy określonej niezależnie od swojej klasy nadrzędnej lub podklasy. |

Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` najlepszą wydajność.

`pCtx`  
[in] Ta wartość jest zazwyczaj `null`. W przeciwnym razie jest wskaźnik do [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy. 

`ppEnum`  
[out] Jeśli nie występują błędy, uzyskuje wskaźnik do moduł wyliczający, który umożliwia obiekt wywołujący, aby pobrać wystąpień w zestawie wyników kwerendy. Zapytania mogą mieć zestaw wyników z wystąpień zero. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

`authLevel`  
[in] Poziom autoryzacji.

`impLevel`[in] Poziom personifikacji.

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
| `WBEM_E_INVALID_QUERY` | 0x80041017 | Zapytania wystąpił błąd składni. |
| `WBEM_E_INVALID_QUERY_TYPE` | 0x80041018 | Żądany język kwerendy nie jest obsługiwane. |
| `WBEM_E_QUOTA_VIOLATION` | 0x8004106c | Zapytanie jest zbyt złożony. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do wykonania operacji. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Usługa WMI jest prawdopodobnie zatrzymana i ponownie uruchomić. Wywołanie [ConnectServerWmi](connectserverwmi.md) ponownie. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Procedury zdalnej łącze wywołań (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Kwerenda Określa klasę, która nie istnieje. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemServices::ExecQuery](https://msdn.microsoft.com/library/aa392107(v=vs.85).aspx) metody.

Ta funkcja przetwarza zapytanie określone w `strQuery` parametru i tworzy moduł wyliczający, przez który wywołującego mogą uzyskiwać dostęp do wyników zapytania. Moduł wyliczający jest wskaźnik do [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) interfejsu; zapytanie wyniki są wystąpieniami klasy obiektów dostępne za pośrednictwem [IWbemClassObject](https://msdn.microsoft.com/library/aa391433(v=vs.85).aspx) interfejsu.

Istnieją ograniczenia liczby `AND` i `OR` słów kluczowych, które mogą być używane w zapytaniach WQL. Dużą liczbą słów kluczowych języka WQL używanych w zapytaniu złożonych może spowodować WMI do zwrócenia `WBEM_E_QUOTA_VIOLATION` (lub 0x8004106c) kod błędu jako `HRESULT` wartość. Limit słów kluczowych języka WQL zależy od tego, jak złożoność zapytanie jest.

Jeśli wystąpi błąd wywołania funkcji, można uzyskać dodatkowe informacje o błędzie przez wywołanie metody [GetErrorInfo](geterrorinfo.md) funkcji.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
