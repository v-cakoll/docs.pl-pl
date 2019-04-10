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
ms.openlocfilehash: b6fa729b131d12b2825a2def700fd918ce8acc40
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220178"
---
# <a name="callid-structure"></a>CALL_ID — Struktura
Informacje debugera o funkcję, która jest wywoływana. Zobacz [inotifysink2 —](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interfejsu, aby uzyskać więcej informacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
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

- [INotifySink2 — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [Struktury magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
