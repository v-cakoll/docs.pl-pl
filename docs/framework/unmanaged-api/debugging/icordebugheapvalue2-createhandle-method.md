---
title: ICorDebugHeapValue2::CreateHandle — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da5c5a12df5689f113857045ba4bcda696bda8f5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756726"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle — Metoda
Tworzy dojście do określonego typu dla wartości sterty, reprezentowane przez ten obiekt icordebugheapvalue2 —.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `type`  
 [in] Wartość cordebughandletype — wyliczenie, który określa typ dojścia do utworzenia.  
  
 `ppHandle`  
 [out] Wskaźnik na adres icordebughandlevalue — obiekt, który reprezentuje nowy uchwyt dla tej wartości na stosie.  
  
## <a name="remarks"></a>Uwagi  
 Dojście zostaną utworzone w domenie aplikacji, która jest skojarzona z wartością sterty i staną się nieprawidłowe, jeśli domena aplikacji zostanie zwolniona.  
  
 Spowoduje to utworzenie wielu wywołań tej funkcji dla tej samej wartości sterty obsługuje wiele. Ponieważ uchwyty wpływa na wydajność modułu odśmiecania pamięci, debuger należy ograniczyć do stosunkowo małej liczby dojść (około 256), które są aktywne w danym momencie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
