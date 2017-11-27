---
title: "ICorDebugAppDomain::IsAttached — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.IsAttached
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a85b674ad705f77e00cf2a8a5286d6a74f7a646
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainisattached-method"></a>ICorDebugAppDomain::IsAttached — Metoda
Pobiera wartość wskazującą, czy debuger jest dołączony do domeny aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbAttached`  
 [out] `true` Jeśli Debuger jest dołączony do domeny aplikacji; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Nie można używać metod ICorDebugController, dopóki nie dołącza debuger do domeny aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
