---
title: funkcja QualifierSet_EndEnumeration (odwołanie do interfejsu API niezarządzanego)
description: Funkcja QualifierSet_EndEnumeration kończy wyliczenie.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c606580ff2e02c5659c14b134b1a17a65651952b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176750"
---
# <a name="qualifierset_endenumeration-function"></a>QualifierSet_EndEnumeration funkcja
Kończy wyliczenie rozpoczęte wywołaniem funkcji [QualifierSet_BeginEnumeration.](qualifierset-beginenumeration.md)  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr
);
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[w] Ten parametr jest nieużywane.

`ptr`[w] Wskaźnik do [wystąpienia IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)

## <a name="return-value"></a>Wartość zwracana

Następująca wartość zwracana przez tę funkcję jest zdefiniowana w pliku nagłówkowym *WbemCli.h* lub można zdefiniować ją jako stałą w kodzie:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie [metody IWbemQualifierSet::EndEnumeration.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration)

To wywołanie jest zalecane, ale nie jest wymagane. Natychmiast zwalnia zasoby skojarzone z wyliczeniem.

## <a name="requirements"></a>Wymagania  

**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
**Nagłówek:** WMINet_Utils.idl  
  
**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
