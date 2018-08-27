---
title: Get — funkcja (niezarządzany wykaz interfejsów API)
description: Funkcja Get pobiera wartość określonej właściwości.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb7475623961fe2ee5fc821c5f237f0a2acfae1a
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933336"
---
# <a name="get-function"></a>Get — funkcja
Pobiera wartość określonej właściwości, jeśli taki istnieje.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
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

`wszName`  
[in] Nazwa właściwości.

`lFlags` [in] Zastrzeżone. Ten parametr musi być 0.

`pVal` [out] Jeśli funkcja zwraca pomyślnie, zawiera wartość `wszName` właściwości. `pval` Argument jest przypisany poprawny typ i wartość kwalifikatora.

`pvtType` [out] Jeśli funkcja zwraca pomyślnie, zawiera [stałą typu modelu wspólnych informacji](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) oznacza typ właściwości. Wartość może być również `null`. 

`plFlavor` [out] Jeśli funkcja zwraca pomyślnie, otrzymuje informacje na temat źródła właściwości. Wartość może być `null`, lub jeden z następujących stałych WBEM_FLAVOR_TYPE zdefiniowane w *WbemCli.h* pliku nagłówka: 

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Właściwość jest właściwością standardowych systemowych. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Dla klasy: właściwość jest dziedziczona z klasy nadrzędnej. </br> W przypadku wystąpienia: właściwość, podczas gdy dziedziczone z klasy nadrzędnej, nie został zmodyfikowany przez to wystąpienie.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Dla klasy: właściwość należy do klasy pochodnej. </br> W przypadku wystąpienia: Ta właściwość jest modyfikowana przez wystąpienie; oznacza to, że podano wartość lub kwalifikator został dodany lub zmodyfikowany. |

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden lub więcej parametrów są nieprawidłowe. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nie znaleziono określonej właściwości. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) metody.

`Get` Funkcji może również zwracać właściwości systemu.

`pVal` Argument jest przypisany poprawny typ i wartość kwalifikatora i COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) — funkcja

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
