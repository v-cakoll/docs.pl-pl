---
title: COR_ACTIVE_FUNCTION — Struktura
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0400da0cd29d642a1be42be7e2b22213ae54b94
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121774"
---
# <a name="coractivefunction-structure"></a>COR_ACTIVE_FUNCTION — Struktura
Zawiera informacje na temat funkcji, które są aktualnie aktywne w ramkach w wątku. Ta struktura jest używany przez [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`pAppDomain`|Wskaźnik do właściciela domeny aplikacji `ilOffset` pola.|  
|`pModule`|Wskaźnik do właściciela modułu `ilOffset` pola.|  
|`pFunction`|Wskaźnik do funkcji właściciela `ilOffset` pola.|  
|`ilOffset`|Przesunięcia języka pośredniego (MSIL) firmy Microsoft ramki.|  
|`flags`|Zarezerwowane dla przyszłej rozszerzalności.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
