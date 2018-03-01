---
title: "ICorDebugHeapValue2::CreateHandle — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eeef3215c3740cdaa7d1b78b73fde9e76d7b40c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle — Metoda
Tworzy dojście o określonym typie dla wartości sterty reprezentowany przez ten obiekt ICorDebugHeapValue2.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 [in] Wartość wyliczenia CorDebugHandleType, która określa typ dojścia do utworzenia.  
  
 `ppHandle`  
 [out] Wskaźnik do adres obiektu ICorDebugHandleValue reprezentujący nowy uchwyt dla tej wartości stosu.  
  
## <a name="remarks"></a>Uwagi  
 Dojście zostaną utworzone w domenie aplikacji, które jest skojarzone z wartością sterty i staną się nieprawidłowe, jeśli domena aplikacji zostanie usunięty z pamięci.  
  
 Wiele wywołań tej funkcji dla tej samej wartości sterty spowoduje utworzenie wielu dojść. Ponieważ uchwytów wpływ na wydajność modułu zbierającego elementy bezużyteczne, debuger ograniczyć się do stosunkowo małej liczby dojść (około 256), które są aktywne w czasie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
