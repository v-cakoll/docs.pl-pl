---
title: "Funkcja Next (niezarządzany wykaz interfejsów API)"
description: "Następny funkcja retireves dalej właściwości w wyliczeniu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Next
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Next
helpviewer_keywords: Next function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c198a9f9507af583f4718c636cd00c9d65a25695
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="next-function"></a>Funkcja Next
Pobiera dalej właściwości w wyliczeniu zaczyna się od wywołania [Beingenumeration](beginenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor     
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.

`lFlags`  
[in] Zastrzeżone. Ten parametr musi wynosić 0.

`pstrName`  
[out] Nowy `BSTR` zawiera nazwę właściwości. Ustaw ten parametr, `null` Jeśli nazwa nie jest wymagana.

`pVal`  
[out] A `VARIANT` wypełnione wartością właściwości. Ustaw ten parametr, `null` Jeśli wartość nie jest wymagana. Jeśli funkcja zwraca błąd o kodzie `VARIANT` przekazany do `pVal` jest lewej nie mają być modyfikowane. 

`pvtType`  
[out] Wskaźnik do `CIMTYPE` zmiennej ( `LONG` do znajduje się typ właściwości). Wartość tej właściwości może być `VT_NULL_VARIANT`, w którym to przypadku należy określić rzeczywisty typ właściwości. Ten parametr może również być `null`. 

`plFlavor`  
[out] `null`, lub wartość, która otrzymuje informacje o pochodzeniu właściwości. W sekcji [Uwagi] możliwych wartości. 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Nie znaleziono żadnych wywołanie [ `BeginEnumeration` ](beginenumeration.md) funkcji. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Można rozpocząć nowego wyliczenia jest za mało pamięci. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Zdalne wywoływanie procedur między bieżącym procesem a zarządzania systemu Windows nie powiodło się. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Nie ma żadnych więcej właściwości w wyliczeniu. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::Next](https://msdn.microsoft.com/library/aa391453(v=vs.85).aspx) metody.

Ta metoda zwraca również wartość właściwości systemu.

W przypadku ścieżkę obiektu, datę lub godzinę innego specjalny typ podstawowy typu właściwości zwrócony typ nie zawiera wystarczających informacji. Obiekt wywołujący musi zbadać `CIMTYPE` dla określonej właściwości ustalić, czy właściwość jest odwołanie do obiektu, datę lub godzinę innego typu specjalne.

Jeśli `plFlavor` nie jest `null`, `LONG` wartość otrzymuje informacje o pochodzeniu właściwości, w następujący sposób:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Właściwość jest właściwością standardowy system. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Dla klasy: właściwość jest dziedziczona z klasy nadrzędnej. </br> Dla wystąpienia obiektu: właściwości, podczas gdy dziedziczone z klasy nadrzędnej, nie został zmodyfikowany przez to wystąpienie.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Dla klasy: właściwość należy do klasy pochodnej. </br> Dla wystąpienia obiektu: właściwość jest modyfikowany przez wystąpienie; oznacza to, że podano wartości lub kwalifikator został dodany lub zmodyfikowany. |

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
