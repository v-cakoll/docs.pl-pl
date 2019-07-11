---
title: CALL_ID — Struktura
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2823c018ff22607052cb9a298f69dbd0c4fe2c23
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769500"
---
# <a name="callid-structure"></a>CALL_ID — Struktura
Informacje debugera o funkcję, która jest wywoływana. Zobacz [inotifysink2 —](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interfejsu, aby uzyskać więcej informacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`szMachine`|Identyfikuje komputer, który wykonuje wywołanie.|  
|`dwPid`|Określa procesor maszyny.|  
|`pUserThread`|Identyfikuje wątku, który wykonuje wywołanie.|  
|`addrStackPointer`|Określa adres stosu wywołań.|  
|`szEntryPoint`|Określa adres wywołania.|  
|`szDestinationMachine`|Identyfikuje komputer, na którym będą wykonywane wywołanie.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Zobacz także

- [INotifySink2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [Struktury magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
