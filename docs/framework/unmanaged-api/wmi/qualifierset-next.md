---
title: Funkcja QualifierSet_Next (niezarządzany wykaz interfejsów API)
description: Funkcja QualifierSet_Next pobiera następny kwalifikatora w wyliczeniu.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 938044a4e932139eb8a4d0a5d2f998cbc6f193cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507696"
---
# <a name="qualifiersetnext-function"></a>QualifierSet_Next — funkcja
Pobiera następny kwalifikatora w wyliczeniu, który uruchamiany przy użyciu wywołania do [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkcji.   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`   
[in] Ten parametr jest nieużywany.

`ptr`   
[in] Wskaźnik do [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) wystąpienia.

`lFlags`   
[in] Zastrzeżone. Ten parametr musi być 0.

`pstrName`   
[out] Nazwa kwalifikatora. Jeśli `null`, ten parametr jest ignorowane; w przeciwnym razie `pstrName` nie powinien wskazywać do prawidłowego `BSTR` lub występuje przeciek pamięci. Jeśli nie ma wartości null, funkcja zawsze przydziela nową `BSTR` zwróceniem `WBEM_S_NO_ERROR`.

`pVal`   
[out] Jeśli operacja się powiedzie, wartość kwalifikatora. Jeśli funkcja zawiedzie, `VARIANT` wskazywany przez `pVal` nie jest modyfikowany. Jeśli ten parametr jest `null`, parametr jest ignorowany.

`plFlavor`   
[out] Wskaźnik na wartość typu LONG, który odbiera wersja kwalifikatora. Jeśli informacje o wersji nie jest wymagana, ten parametr może być `null`. 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Obiekt wywołujący nie wywołał [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny rozpocząć nowe wyliczenie. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Nie więcej kwalifikatorów są pozostawiane w wyliczeniu. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) metody.

Należy wywołać `QualifierSet_Next` funkcja wielokrotnie wyliczyć wszystkie kwalifikatory aż zwrot funkcji `WBEM_S_NO_MORE_DATA`. Aby zakończyć wyliczenia wcześnie, należy wywołać [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) funkcji.

Kolejność kwalifikatory zwrócony podczas wyliczania jest niezdefiniowane.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
