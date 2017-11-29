---
title: "ICorDebugEval::GetResult — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.GetResult
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7379237c73d79d9e8c66112a101edadca357cb10
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult — Metoda
Pobiera wyniki tej oceny.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppResult`  
 [out] Wskaźnik do adresu ICorDebugValue obiektu, który reprezentuje wyniki tej oceny oceny wykona normalnie.  
  
## <a name="remarks"></a>Uwagi  
 `GetResult` Metoda jest prawidłowa tylko po zakończeniu okresu ewaluacyjnego.  
  
 Obliczanie wykona zwykle `ppResult` określa wyniki. Jeśli zostaje zakończone z powodu wyjątku, wynikiem jest zgłoszony wyjątek. Jeśli ocena dla nowego obiektu, wynikiem jest odwołanie do nowego obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
