---
title: "ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 560690e95e7aa0aef37e3a708183641bd70ee97d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a>ISymUnmanagedAsyncMethod::IsAsyncMethod — Metoda
Sprawdza, czy metoda ma informacje o asynchronicznej.  
  
 Jeśli ta metoda zwraca `FALSE` , a następnie jest wywoływać inne metody w tym interfejsie. One będą zwracane wszystkie `E_UNEXPECTED` w takim przypadku.  
  
## <a name="syntax"></a>Składnia  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `HRESULT`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedAsyncMethod, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
