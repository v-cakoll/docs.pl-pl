---
title: Funkcja umieszczania (niezarządzany wykaz interfejsów API)
description: Funkcję Put przypisuje nową wartość o nazwie właściwości.
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
ms.openlocfilehash: 1ec8fe889885b555cbf9a95cd34b7330efff27f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43460988"
---
# <a name="put-function"></a>Umieść — funkcja
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
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`wszName`  
[in] Nazwa właściwości. Ten parametr nie może być `null`.

`lFlags`  
[in] Zastrzeżone. Ten parametr musi być 0.

`pVal`   
[in] Wskaźnik do prawidłowego `VARIANT` stanie się nowa wartość właściwości. Jeśli `pVal` jest `null` lub wskazuje na `VARIANT` typu `VT_NULL`, zostaje ustalona `null`. 

`vtType`  
[in] Typ `VARIANT` wskazywany przez `pVal`. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.
 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden lub więcej parametrów są nieprawidłowe. |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | Nie rozpoznano typu właściwości. Ta wartość jest zwracana podczas tworzenia wystąpienia klasy, jeśli klasa już istnieje. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | Dla wystąpień: oznacza, że `pVal` wskazuje `VARIANT` nieprawidłowego typu właściwości. <br/> Aby uzyskać definicje klas: właściwość już istnieje w klasie nadrzędnej, a nowy typ COM jest inny niż stary typ COM. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) metody.

Ta funkcja zawsze zastępuje bieżącą wartość właściwości nowej. Jeśli [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) punkty na definicję klasy `Put` tworzy lub aktualizuje wartości właściwości. Gdy [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskazuje na wystąpienie CIM `Put` aktualizuje wartości właściwości. `Put` nie można utworzyć wartości właściwości.

`__CLASS` System właściwość jest tylko zapisu podczas tworzenia klasy, gdy go nie może pozostać puste. Wszystkie pozostałe właściwości systemu są tylko do odczytu.

Użytkownik nie można utworzyć właściwości z nazwami będącymi rozpoczynać się ani kończyć znakiem podkreślenia ("_"). Jest on zarezerwowany dla klas systemowych i właściwości.

Jeśli właściwość jest ustawiona `Put` istnieje funkcja w klasie nadrzędnej, wartość domyślna właściwości zostanie zmieniona, chyba że typ właściwości jest niezgodny z typem klasy nadrzędnej. Jeśli właściwość nie istnieje, nie jest niezgodność typu właściwości jest ceated.

Użyj `vtType` parametru tylko podczas tworzenia nowych właściwości w definicji klasy modelu wspólnych informacji i `pVal` jest `null` lub wskazuje na `VARIANT` typu `VT_NULL`. W tym przypadku `vType` parametr określa typ CIM właściwości. W każdym przypadku `vtType` musi mieć wartość 0. `vtType` musi również być na 0, jeśli obiekt źródłowy jest wystąpieniem (nawet jeśli `Val` jest `null`), ponieważ typ właściwości jest stała i nie można jej zmienić.   

## <a name="example"></a>Przykład

Aby uzyskać przykład, zobacz [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
