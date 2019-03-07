---
title: ICorDebugEval::GetResult — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8e7fcb4f44d6bdf6f18c93b1046b549331621a4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470799"
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult — Metoda
Pobiera wyniki tej oceny.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppResult`  
 [out] Wskaźnik na adres obiektu ICorDebugValue, który reprezentuje wyniki tej oceny, jeśli oceny zakończy się normalnie.  
  
## <a name="remarks"></a>Uwagi  
 `GetResult` Metoda jest prawidłowa tylko w przypadku, po zakończeniu okresu ewaluacyjnego.  
  
 Jeśli ocena zakończy się normalnie, `ppResult` określa wyniki. Jeśli kończy się z powodu wyjątku, wynik jest zgłoszony wyjątek. Jeśli ocena dla nowego obiektu, wynik jest odwołanie do nowego obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
