---
title: ICorDebugAssembly — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2b802845e36e818a962484c1fea09cbcc1ceefd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974578"
---
# <a name="icordebugassembly-interface"></a>ICorDebugAssembly — Interfejs

Reprezentuje zestaw.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateModules, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|Pobiera moduł wyliczający dla modułów są zawarte w zestawie.|  
|[GetAppDomain, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|Pobiera wskaźnik interfejsu do domeny aplikacji, która zawiera to `ICorDebugAssembly` wystąpienia.|  
|[GetCodeBase, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|Nie jest zaimplementowany w bieżącej wersji programu .NET Framework.|  
|[GetName, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|Pobiera nazwę zestawu.|  
|[GetProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|Pobiera wystąpienie ICorDebugProcess, w którym uruchomiony jest zestaw.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
