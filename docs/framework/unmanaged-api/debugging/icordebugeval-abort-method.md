---
title: ICorDebugEval::Abort — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.Abort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type:
- apiref
ms.openlocfilehash: 98a9b285323bc3ad94b4f555e72a4b3242519801
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976294"
---
# <a name="icordebugevalabort-method"></a>ICorDebugEval::Abort — Metoda
Przerywa obliczenia wykonywane przez ten obiekt ICorDebugEval.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ocena jest zagnieżdżona i nie jest to najnowsza z nich, `Abort` Metoda może zakończyć się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
