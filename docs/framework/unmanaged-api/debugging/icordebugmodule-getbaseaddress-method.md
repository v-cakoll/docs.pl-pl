---
title: ICorDebugModule::GetBaseAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 763f2872099fac87138b7e1ab058c60475892b0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107422"
---
# <a name="icordebugmodulegetbaseaddress-method"></a>ICorDebugModule::GetBaseAddress — Metoda
Pobiera adres podstawowy moduł.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAddress`  
 [out] A `CORDB_ADDRESS` określający adres podstawowy moduł.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli moduł jest natywny obraz (to znaczy, jeśli moduł został wyprodukowany przez generator obrazu natywnego, NGen.exe), jej adres podstawowy będzie mieć wartość zero.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
