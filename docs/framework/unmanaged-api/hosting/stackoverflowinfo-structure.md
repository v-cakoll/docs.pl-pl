---
title: StackOverflowInfo — Struktura
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1e652588d27521a04015228e86eb9af9c53346e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440817"
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
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
