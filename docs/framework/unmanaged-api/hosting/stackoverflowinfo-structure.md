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
ms.openlocfilehash: 7de5a6d38d43c20ce52f609ef6514a1f28022416
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781135"
---
# <a name="stackoverflowinfo-structure"></a>StackOverflowInfo — Struktura
Typ przepełnienia, które wystąpiły, oraz informacje są przechowywane na wyjątek, który został wygenerowany z powodu przepełnienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`soType`|Wartość [stackoverflowtype —](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) wyliczenie, który określa typ przepełnienia.|  
|`pExceptionInfo`|Wskaźnik do systemu Win32 `EXCEPTION_POINTERS` obiekt, który zawiera rekord wyjątku z opisem wyjątku niezależne od komputera i rekordu kontekstu z opisem zależnych od maszyny kontekst procesora w czasie wystąpienia wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 A `StackOverflowInfo` obiekt jest przekazywany do [iactiononclrevent::ONEVENT —](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodę `Event_StackOverflow` zdarzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
