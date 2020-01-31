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
ms.openlocfilehash: 197c33511a474eb8291e4361ebb3c21fb3720cae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789430"
---
# <a name="cordebugehclause-structure"></a>Struktura CorDebugEHClause
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Reprezentuje klauzulę obsługi wyjątków (EH) dla danego fragmentu kodu języka pośredniego (IL).  
  
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
|`Flags`|Pole bitowe opisujące informacje o wyjątku w klauzuli EH. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|  
|`TryOffset`|Przesunięcie, w bajtach, bloku `try` od początku treści metody.|  
|`TryLength`|Długość (w bajtach) bloku `try`.|  
|`HandlerOffset`|Lokalizacja programu obsługi dla tego bloku `try`.|  
|`HandlerLength`|Rozmiar kodu programu obsługi w bajtach.|  
|`ClassToken`|Token metadanych dla obsługi wyjątków opartych na typie.|  
|`FilterOffset`|Przesunięcie, w bajtach, od początku treści metody dla procedury obsługi wyjątków opartej na filtrze.|  
  
## <a name="remarks"></a>Uwagi  
 Tablica wartości `CoreDebugEHClause` jest zwracana przez metodę [GetEHClauses](icordebugilcode-getehclauses-method.md) .  
  
 Informacje o klauzuli EH są definiowane przez specyfikację interfejsu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [standardowe ECMA-355: infrastruktury języka wspólnego (CLI), w wersji 6](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 Pole `flags` może zawierać następujące flagi. Należy zauważyć, że nie są one zdefiniowane w CorDebug. idl lub CorDebug. h.  
  
|Flaga|Wartość|Opis|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|0x00000000|Klauzula wyjątku o określonym typie.|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|0x00000001|Filtr wyjątku i klauzula obsługi.|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|0x00000002|Klauzula `finally`.|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|0x00000004|Klauzula błędu (klauzula `finally`, która jest wywoływana tylko w przypadku zgłoszenia wyjątku).|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetEHClauses, metoda](icordebugilcode-getehclauses-method.md)
- [Struktury debugowania](debugging-structures.md)
