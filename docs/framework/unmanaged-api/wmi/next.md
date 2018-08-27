---
title: Użycie funkcji Next (niezarządzany wykaz interfejsów API)
description: Dalej funkcja retireves następną właściwość w wyliczeniu.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15d470ccf9384695aa38a50c2c062c1b660fea96
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934976"
---
# <a name="next-function"></a>Użycie funkcji Next
Pobiera następną właściwość w wyliczenie, które zaczyna się od wywołania [Beingenumeration](beginenumeration.md).  

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
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`lFlags`  
[in] Zastrzeżone. Ten parametr musi być 0.

`pstrName`  
[out] Nowy `BSTR` zawierający nazwę właściwości. Ten parametr zostanie ustawiony na `null` Jeśli nazwa nie jest wymagana.

`pVal`  
[out] A `VARIANT` wypełnione wartością właściwości. Ten parametr zostanie ustawiony na `null` Jeśli wartość nie jest wymagana. Jeśli funkcja zwraca kod błędu: `VARIANT` przekazany do `pVal` się po lewej stronie w niezmienionej postaci. 

`pvtType`  
[out] Wskaźnik do `CIMTYPE` zmiennej ( `LONG` do jest umieszczany typ właściwości). Wartość tej właściwości może być `VT_NULL_VARIANT`, w którym to przypadku należy określić rzeczywisty typ właściwości. Ten parametr może być również `null`. 

`plFlavor`  
[out] `null`, lub wartość, która otrzymuje informacje o pochodzeniu właściwości. W sekcji [Uwagi] możliwych wartości. 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Wystąpił brak wywołania [ `BeginEnumeration` ](beginenumeration.md) funkcji. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny rozpocząć nowe wyliczenie. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Zdalne wywoływanie procedur z przedziału od bieżącym procesem a usługą Windows Management nie powiodło się. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Nie ma żadnych więcej właściwości w wyliczeniu. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) metody.

Ta metoda zwraca również wartość właściwości systemu.

W przypadku ścieżki obiektu, daty lub godziny lub innego specjalny typ podstawowy typu właściwości zwracany typ nie zawiera wystarczającej ilości informacji. Obiekt wywołujący należy zbadać `CIMTYPE` dla określonej właściwości w celu ustalenia, czy właściwość jest odwołanie do obiektu, daty lub godziny lub innego typu specjalne.

Jeśli `plFlavor` nie `null`, `LONG` wartość otrzymuje informacje na temat źródła właściwości, w następujący sposób:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Właściwość jest właściwością standardowych systemowych. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Dla klasy: właściwość jest dziedziczona z klasy nadrzędnej. </br> W przypadku wystąpienia: właściwość, podczas gdy dziedziczone z klasy nadrzędnej, nie został zmodyfikowany przez to wystąpienie.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Dla klasy: właściwość należy do klasy pochodnej. </br> W przypadku wystąpienia: Ta właściwość jest modyfikowana przez wystąpienie; oznacza to, że podano wartość lub kwalifikator został dodany lub zmodyfikowany. |

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
