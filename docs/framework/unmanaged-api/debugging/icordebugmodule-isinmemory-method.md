---
title: ICorDebugModule::IsInMemory — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ae5c16f9f508511e4a15b2eae2c28d68238f1d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415896"
---
# <a name="icordebugmoduleisinmemory-method"></a>ICorDebugModule::IsInMemory — Metoda
Pobiera wartość wskazującą, czy ten moduł istnieje tylko w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pInMemory`  
 [out] `true` Jeśli ten moduł istnieje tylko w pamięci; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje ładowanie modułów raw strumienie bajtów. Takie moduły są nazywane *modułów w pamięci* i nie istnieje na dysku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
    
 
