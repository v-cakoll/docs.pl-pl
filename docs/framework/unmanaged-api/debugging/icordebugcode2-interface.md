---
title: ICorDebugCode2 Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13803a8cc292da602b1b920a3879120c3e754ca4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414561"
---
# <a name="icordebugcode2-interface1"></a>ICorDebugCode2 Interface1
Udostępnia metody, które rozszerzają możliwości "ICorDebugCode".  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCodeChunks, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|Pobiera fragmentów kodu, który składa się ten obiekt kodu z.|  
|[GetCompilerFlags, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|Pobiera flagi, które określają warunki, na których ten obiekt kodu zostało albo just-in-time (JIT) kompilacji lub wygenerowanych przy użyciu generator obrazu natywnego (Ngen.exe).|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
    
 [ICorDebugCode3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
