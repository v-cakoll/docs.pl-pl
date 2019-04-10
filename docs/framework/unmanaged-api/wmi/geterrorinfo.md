---
title: Geterrorinfo — funkcja (niezarządzany wykaz interfejsów API)
description: Funkcja geterrorinfo — pobiera informacje o błędzie z poprzedniego wywołania funkcji.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2df4b87016394d1998ef90abe2e3eeb911886ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217508"
---
# <a name="geterrorinfo-function"></a>Geterrorinfo — funkcja
Pobiera informacje o błędzie z poprzedniego wywołania funkcji.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) obiektu, jeśli wywołanie funkcji zakończy się pomyślnie, lub `null` Jeśli zakończy się niepowodzeniem.
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.def  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
