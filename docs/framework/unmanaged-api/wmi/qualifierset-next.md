---
title: "Funkcja QualifierSet_Next (niezarządzany wykaz interfejsów API)"
description: Funkcja QualifierSet_Next pobiera kwalifikator dalej w wyliczeniu.
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 01a9c9d162039547849597aaa9c8a6fa38a31455
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetnext-function"></a>Funkcja QualifierSet_Next
Pobiera kwalifikator dalej w wyliczeniu, który uruchomił się wywołaniem do [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkcji.   

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
[in] Ten parametr nie jest używana.

`ptr`   
[in] Wskaźnik do [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) wystąpienia.

`lFlags`   
[in] Zastrzeżone. Ten parametr musi wynosić 0.

`pstrName`   
[out] Nazwa kwalifikatora. Jeśli `null`, ten parametr jest ignorowana, a w przeciwnym razie `pstrName` nie powinny wskazywać na prawidłową `BSTR` lub występuje przeciek pamięci. Jeśli nie jest wartość null, funkcja zawsze przydziela nowy `BSTR` po zwraca `WBEM_S_NO_ERROR`.

`pVal`   
[out] Gdy to się powiedzie, wartość kwalifikator. W przypadku niepowodzenia funkcji `VARIANT` wskazywana przez `pVal` nie jest modyfikowany. Jeśli ten parametr ma `null`, parametr będzie ignorowany.

`plFlavor`   
[out] Wskaźnik do LONG, który odbiera podtyp kwalifikator. Jeśli informacje o wersji nie jest wymagana, ten parametr może być `null`. 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Obiekt wywołujący nie wywołał [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Można rozpocząć nowego wyliczenia jest za mało pamięci. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Nie więcej kwalifikatory są pozostawiane w wyliczeniu. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) metody.

Należy wywołać `QualifierSet_Next` funkcja wielokrotnie wyliczyć wszystkie kwalifikatory do zwrot funkcji `WBEM_S_NO_MORE_DATA`. Zakończenie wczesne wyliczenia, wywołaj [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) funkcji.

Kolejność kwalifikatory zwrócony podczas wykonywania wyliczenia jest niezdefiniowana.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
