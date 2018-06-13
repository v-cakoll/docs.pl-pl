---
title: Funkcja Put (niezarządzany wykaz interfejsów API)
description: Funkcja Put przypisuje nową wartość do nazwanej właściwości.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f3ffe27bef6583b733fc04f2f25903d545daa74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460382"
---
# <a name="put-function"></a>Put — funkcja
Ustawia właściwość o nazwie na nową wartość.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Put (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.

`wszName`  
[in] Nazwa właściwości. Ten parametr nie może być `null`.

`lFlags`  
[in] Zastrzeżone. Ten parametr musi wynosić 0.

`pVal`   
[in] Wskaźnik do prawidłowej `VARIANT` jako nowa wartość właściwości. Jeśli `pVal` jest `null` lub wskazuje `VARIANT` typu `VT_NULL`, ma ustawioną właściwość `null`. 

`vtType`  
[in] Typ `VARIANT` wskazywana przez `pVal`. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.
 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden lub więcej parametrów nie są prawidłowe. |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | Nie rozpoznano typu właściwości. Ta wartość jest zwracana w trakcie tworzenia wystąpień klasy, jeśli klasa już istnieje. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do wykonania operacji. |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | Dla wystąpień: wskazuje, że `pVal` wskazuje `VARIANT` niepoprawnego typu dla właściwości. <br/> Dla definicji klasy: właściwość już istnieje w klasie nadrzędnej, a nowy typ COM różni się od starego typu COM. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) metody.

Ta funkcja zastępuje zawsze bieżącą wartość właściwości nowej. Jeśli [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wskazuje definicję klasy `Put` tworzy lub aktualizuje wartość właściwości. Gdy [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wskazuje na wystąpienie CIM, `Put` aktualizacji wartości właściwości. `Put` nie można utworzyć wartości właściwości.

`__CLASS` Systemu właściwość jest tylko zapisu podczas tworzenia klasy, jeśli go nie może pozostać puste. Wszystkie inne właściwości systemu są tylko do odczytu.

Użytkownik nie można utworzyć właściwości o nazwach rozpoczynać się ani kończyć znakiem podkreślenia ("_"). Jest to zarezerwowana dla systemu klas i właściwości.

Jeśli właściwość jest ustawiona `Put` funkcja istnieje w klasie nadrzędnej, wartością domyślną właściwości zostanie zmieniona, chyba że typ właściwości nie jest zgodny z typem klasy nadrzędnej. Jeśli właściwość nie istnieje i nie jest niezgodność typów, właściwość jest ceated.

Użyj `vtType` parametru tylko podczas tworzenia nowych właściwości w definicji klasy modelu wspólnych informacji i `pVal` jest `null` lub wskazuje `VARIANT` typu `VT_NULL`. W takim przypadku `vType` parametr określa typ CIM właściwości. W każdym przypadku `vtType` musi być równa 0. `vtType` również musi wynosić 0, jeśli obiekt jest wystąpieniem (nawet jeśli `Val` jest `null`), ponieważ typ właściwości jest stała i nie można zmienić.   

## <a name="example"></a>Przykład

Na przykład zobacz [IWbemClassObject::Put](https://msdn.microsoft.com/library/aa391455(v=vs.85).aspx) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
