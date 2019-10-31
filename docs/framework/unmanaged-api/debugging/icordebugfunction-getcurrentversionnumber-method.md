---
title: ICorDebugFunction::GetCurrentVersionNumber — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: 0530ba742a739003bfa33079ad75cb1e6f5f5e59
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124017"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a>ICorDebugFunction::GetCurrentVersionNumber — Metoda
Pobiera numer wersji najnowszej edycji wykonanej do funkcji reprezentowanej przez ten obiekt ICorDebugFunction.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pnCurrentVersion`  
 określoną Wskaźnik do wartości całkowitej, która jest numerem wersji najnowszej edycji wykonanej w tej funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Numer wersji najnowszej edycji tej funkcji może być większy niż numer wersji samej funkcji. Użyj metody [ICorDebugFunction2:: GetVersionNumber —](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) lub [ICorDebugCode:: GetVersionNumber —](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) do pobrania numeru wersji funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
