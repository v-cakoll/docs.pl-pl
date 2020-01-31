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
ms.openlocfilehash: da7c0fb472df89d94fa702a13eff968a4c7e68e3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785043"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain, interfejs

Dostarcza metody do debugowania domen aplikacji. Ten interfejs jest podklasą elementu ICorDebugController.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Attach, metoda](icordebugappdomain-attach-method.md)|Dołącza debuger do domeny aplikacji.|  
|[EnumerateAssemblies, metoda](icordebugappdomain-enumerateassemblies-method.md)|Pobiera moduł wyliczający dla zestawów w domenie aplikacji.|  
|[EnumerateBreakpoints, metoda](icordebugappdomain-enumeratebreakpoints-method.md)|Pobiera moduł wyliczający dla wszystkich aktywnych punktów przerwania w domenie aplikacji.|  
|[EnumerateSteppers, metoda](icordebugappdomain-enumeratesteppers-method.md)|Pobiera moduł wyliczający dla wszystkich aktywnych współdziałań w domenie aplikacji.|  
|[GetID, metoda](icordebugappdomain-getid-method.md)|Pobiera unikatowy identyfikator domeny aplikacji.|  
|[GetModuleFromMetaDataInterface, metoda](icordebugappdomain-getmodulefrommetadatainterface-method.md)|Pobiera obiekt ICorDebugModule z danym interfejsem metadanych.|  
|[GetName, metoda](icordebugappdomain-getname-method.md)|Pobiera nazwę domeny aplikacji.|  
|[GetObject, metoda](icordebugappdomain-getobject-method.md)|Pobiera wskaźnik interfejsu do domeny aplikacji środowiska uruchomieniowego języka wspólnego (CLR).|  
|[GetProcess, metoda](icordebugappdomain-getprocess-method.md)|Pobiera proces zawierający domenę aplikacji.|  
|[IsAttached, metoda](icordebugappdomain-isattached-method.md)|Określa, czy debuger jest dołączony do domeny aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
