---
title: "StackOverflowInfo — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackOverflowInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: StackOverflowInfo
helpviewer_keywords: StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 102f744ecc769a10161cd20767e8e49c838252a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="stackoverflowinfo-structure"></a>StackOverflowInfo — Struktura
Przechowuje typ i przepełnienia, który wystąpił na wyjątek zgłoszony z powodu przepełnienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`soType`|Wartość [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) wyliczenia, która określa typ przepełnienia.|  
|`pExceptionInfo`|Wskaźnik do Win32 `EXCEPTION_POINTERS` obiekt, który zawiera rekord wyjątku z opisem wyjątku niezależne od komputera i rekordu kontekstu z opisem zależne od maszyny kontekst procesora w czasie wystąpienia wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 A `StackOverflowInfo` obiekt jest przekazywany do [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodę `Event_StackOverflow` zdarzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting — struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
