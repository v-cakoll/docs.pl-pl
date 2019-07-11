---
title: ICorDebugModule::GetGlobalVariableValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetGlobalVariableValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd79299dcfdb03b703c2cab214ba448631daa6f2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763481"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a>ICorDebugModule::GetGlobalVariableValue — Metoda
Pobiera wartość określonej zmiennej globalnej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fieldDef`  
 [in] `mdFieldDef` Token, który odwołuje się do metadanych opisujących zmiennej globalnej.  
  
 `ppValue`  
 [out] Wskaźnik na adres obiektu ICorDebugValue, który reprezentuje wartość określonej zmiennej globalnej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
