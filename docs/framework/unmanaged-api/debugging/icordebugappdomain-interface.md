---
title: ICorDebugAppDomain, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40619aa40f9924d94c82541eb8d30790e774a675
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996193"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain, interfejs

Dostarcza metody do debugowania domen aplikacji. Ten interfejs jest podklasą icordebugcontroller —.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Attach, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|Dołącza debuger do domeny aplikacji.|  
|[EnumerateAssemblies, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Pobiera moduł wyliczający dla zestawów w domenie aplikacji.|  
|[EnumerateBreakpoints, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|Pobiera moduł wyliczający dla wszystkich aktywnych punktów przerwania w domenie aplikacji.|  
|[EnumerateSteppers, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|Pobiera moduł wyliczający dla wszystkich aktywnych steppery w domenie aplikacji.|  
|[GetID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|Pobiera unikatowy identyfikator domeny aplikacji.|  
|[GetModuleFromMetaDataInterface, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|Pobiera obiekt icordebugmodule — interfejs określonych metadanych.|  
|[GetName, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|Pobiera nazwę domeny aplikacji.|  
|[GetObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|Pobiera wskaźnik interfejsu do typowych domeny aplikacji języka wspólnego (CLR).|  
|[GetProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|Pobiera proces zawierający domeny aplikacji.|  
|[IsAttached, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|Określa, czy debuger jest dołączony do domeny aplikacji.|  
  
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
