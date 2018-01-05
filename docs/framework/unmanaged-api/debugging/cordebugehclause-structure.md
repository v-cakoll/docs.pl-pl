---
title: Struktura CorDebugEHClause
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugEHClause
api_location: mscordbi.dll
api_type: COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97428837d78c246915381b51fb5005a68518b7bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugehclause-structure"></a>Struktura CorDebugEHClause
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Reprezentuje wyjątek klauzuli (EH) dla danej fragment kodu w języku pośrednim (IL).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`Flags`|Pole bitowe, który opisuje informacje o wyjątku w klauzuli EH. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|  
|`TryOffset`|Przesunięcie, w bajtach z `try` bloku od początku treści metody.|  
|`TryLength`|Długość w bajtach z `try` bloku.|  
|`HandlerOffset`|Lokalizacja programu obsługi dla tego `try` bloku.|  
|`HandlerLength`|Rozmiar kod obsługi w bajtach.|  
|`ClassToken`|Token metadanych dla obsługi wyjątków na podstawie typu.|  
|`FilterOffset`|Przesunięcie w bajtach, od początku treści metody obsługi na podstawie filtru wyjątków.|  
  
## <a name="remarks"></a>Uwagi  
 Tablica `CoreDebugEHClause` wartości zwracane przez [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) metody.  
  
 Informacje klauzuli EH jest zdefiniowany w specyfikacji interfejsu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [standardowe ECMA-355: infrastruktury języka wspólnego (CLI), w wersji 6.](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 `flags` Pole może zawierać następujące flagi. Należy pamiętać, że nie są zdefiniowane w CorDebug.idl lub CorDebug.h.  
  
|Flaga|Wartość|Opis|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|0x00000000|Klauzula typu wyjątku.|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|0x00000001|Wyjątek filtru i obsługi klauzuli.|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|0x00000002|A `finally` klauzuli.|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|0x00000004|Klauzula usterek ( `finally` klauzuli, która jest wywoływana tylko wtedy, gdy jest zgłaszany wyjątek).|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [GetEHClauses, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
