---
title: Funkcja GetErrorInfo (niezarządzane odwołanie do interfejsu API)
description: Funkcja GetErrorInfo pobiera informacje o błędzie z poprzedniego wywołania funkcji.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 802ee66a5be213ac7a599b193ec6de589773ea17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176815"
---
# <a name="geterrorinfo-function"></a>GetErrorInfo, funkcja
Pobiera informacje o błędzie z poprzedniego wywołania funkcji.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [IErrorInfo,](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) jeśli wywołanie `null` funkcji powiedzie się lub jeśli zakończy się niepowodzeniem.
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie metody [IComThreadingInfo::GetErrorInfo.](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.def  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
