---
title: ICorDebugLoadedModule::GetBaseAddress — metoda
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c12ea84f1a706850972b2e404ec52eea3523de7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412639"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a>ICorDebugLoadedModule::GetBaseAddress — metoda
Pobiera adres podstawowy załadować modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [out] Wskaźnik do adres podstawowy załadować modułu.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugLoadedModule, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
