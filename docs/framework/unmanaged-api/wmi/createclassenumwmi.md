---
title: Funkcja CreateClassEnumWmi (niezarządzany wykaz interfejsów API)
description: Funkcja CreateClassEnumWmi zwraca moduł wyliczający dla wszystkich klas, które spełniają określone kryteria.
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f84902586a2b940d52eb6365a141af61af802dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461457"
---
# <a name="createclassenumwmi-function"></a>Funkcja CreateClassEnumWmi
Zwraca moduł wyliczający dla wszystkich klas, które spełniają kryteria określonego zaznaczenia.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
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

`strSuperclass`    
[in] Jeśli nie `null` lub puste, określa nazwę klasy nadrzędnej; modułu wyliczającego zwraca tylko podklasy tej klasy. Jeśli jest `null` lub jest pusty i `lFlags` WBEM_FLAG_SHALLOW, zwraca tylko klasy najwyższego poziomu (klasy z klasy nadrzędnej, nie). Jeśli jest `null` lub jest pusty i `lFlags` jest `WBEM_FLAG_DEEP`, zwraca wszystkie klasy w przestrzeni nazw.

`lFlags`   
[in] Kombinacja flag, które wpływają na działanie tej funkcji. Następujące wartości są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie: 

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | Jeśli zestaw, funkcja pobiera poprawionych kwalifikatorów przechowywane w zlokalizowanych nazw ustawień regionalnych bieżącego połączenia. <br/> Jeśli nie zestawu, funkcja pobiera tylko kwalifikatory przechowywane w przestrzeni nazw bezpośrednim. |
| `WBEM_FLAG_DEEP` | 0 | Wyliczenie zawiera podklasami w hierarchii, ale nie do tej klasy. |
| `WBEM_FLAG_SHALLOW` | 1 | Wyliczenie zawiera tylko czysty wystąpienia tej klasy i wyklucza wszystkie wystąpienia podklas, które dostarczają właściwości nie można odnaleźć w tej klasie. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | Flaga powoduje Półsynchroniczne wywołania. |
| `WBEM_FLAG_FORWARD_ONLY` | 0x20 | Funkcja zwraca tylko do przodu modułu wyliczającego. Zwykle tylko do przodu moduły wyliczające są szybsze i używają mniej pamięci niż wyliczenia z konwencjonalnej, ale nie zezwalają na wywołania [klonowania](clone.md). |
| `WBEM_FLAG_BIDIRECTIONAL` | 0 | WMI zachowuje wskaźników do obiektów w enumration, dopóki ich wydania. | 

Zalecane flagi są `WBEM_FLAG_RETURN_IMMEDIATELY` i `WBEM_FLAG_FORWARD_ONLY` najlepszą wydajność.

`pCtx`  
[in] Ta wartość jest zazwyczaj `null`. W przeciwnym razie jest wskaźnik do [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) wystąpienie, które mogą być używane przez dostawcę, który dostarcza żądanej klasy. 

`ppEnum`  
[out] Uzyskuje wskaźnik do modułu wyliczającego.

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
| `WBEM_E_INVALID_CLASS` | 0x80041010 | `strSuperClass` nie istnieje. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do wykonania operacji. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | Usługa WMI jest prawdopodobnie zatrzymana i ponownie uruchomić. Wywołanie [ConnectServerWmi](connectserverwmi.md) ponownie. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Procedury zdalnej łącze wywołań (procedur RPC) między bieżącym procesem a usługą WMI nie powiodło się. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [metodę IWbemServices::CreateClassEnum](https://msdn.microsoft.com/library/aa392095(v=vs.85).aspx) metody.

Jeśli wystąpi błąd wywołania funkcji, można uzyskać dodatkowe informacje o błędzie przez wywołanie metody [GetErrorInfo](geterrorinfo.md) funkcji.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
