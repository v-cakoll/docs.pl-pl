---
title: Struktura CorDebugEHClause
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be5d580c28a15a58cad6c5a2231d3a87e25c0e7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495348"
---
# <a name="cordebugehclause-structure"></a>Struktura CorDebugEHClause
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Reprezentuje wyjątek obsługi klauzuli (EH) dla danego kodu języka pośredniego (IL).  
  
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
|`TryOffset`|Przesunięcie, w bajtach, z `try` bloku od początku treści metody.|  
|`TryLength`|Długość w bajtach z `try` bloku.|  
|`HandlerOffset`|Lokalizacja programu obsługi dla tego `try` bloku.|  
|`HandlerLength`|Rozmiar kod obsługi w bajtach.|  
|`ClassToken`|Token metadanych w przypadku obsługi na podstawie typu wyjątku.|  
|`FilterOffset`|Przesunięcie w bajtach od początku treści metody obsługi wyjątków na podstawie filtru.|  
  
## <a name="remarks"></a>Uwagi  
 Tablica `CoreDebugEHClause` wartości jest zwracana przez [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) metody.  
  
 Informacje o klauzuli EH jest definiowany przez specyfikację interfejsu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [Standard ECMA-355: Common Language Infrastructure (CLI), wersja 6](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 `flags` Pole może zawierać następujących flag. Należy pamiętać, że nie są zdefiniowane w CorDebug.idl lub CorDebug.h.  
  
|Flaga|Wartość|Opis|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|0x00000000|Klauzula typizowanego wyjątku.|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|0x00000001|Wyjątek filtr i obsługi klauzuli.|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|0x00000002|A `finally` klauzuli.|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|0x00000004|Klauzuli fault ( `finally` klauzula, która jest wywoływana tylko wtedy, gdy zostanie zgłoszony wyjątek).|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [GetEHClauses, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)
- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
