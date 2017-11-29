---
title: "Funkcja QualifierSet_EndEnumeration (niezarządzany wykaz interfejsów API)"
description: "Funkcja QualifierSet_EndEnumeration kończy wyliczenia."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_EndEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_EndEnumeration
helpviewer_keywords: QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7868a0c0ba5abb880af201ce73b35f5ffed6f223
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetendenumeration-function"></a>Funkcja QualifierSet_EndEnumeration
Kończy wyliczenie uruchomione za pomocą wywołania [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkcji.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr nie jest używana.

`ptr`   
[in] Wskaźnik do [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) wystąpienia.

## <a name="return-value"></a>Wartość zwracana

Następującą wartość zwracana przez tę funkcję jest zdefiniowany w *WbemCli.h* pliku nagłówka, lub można zdefiniować ją jako stała w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx) metody.

To wywołanie jest zalecane, ale nie jest wymagane. Natychmiast zwalnia zasoby skojarzone z wyliczenia.

## <a name="requirements"></a>Wymagania  

**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
**Nagłówek:** WMINet_Utils.idl  
  
**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
