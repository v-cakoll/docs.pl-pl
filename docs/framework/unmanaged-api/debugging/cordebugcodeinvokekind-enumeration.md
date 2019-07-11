---
title: Wyliczenie CorDebugCodeInvokeKind
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 059e823110686a2b939c9664fa5b67e4041c3486
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740313"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>Wyliczenie CorDebugCodeInvokeKind
W tym artykule opisano, jak eksportowanych funkcji wywołuje kod zarządzany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|Jeśli żadnego kodu zarządzanego wywoływaną przez tę metodę, ma znajdować się później przez jawne zdarzenia lub punkty przerwania.<br /><br /> --lub--<br /><br /> Możemy po prostu pominąć część kodu zarządzanego, które wywołuje ta metoda, ponieważ nie istnieje łatwy sposób można zatrzymać na nim.<br /><br /> --lub--<br /><br /> Metoda nigdy nie mogą wywoływać kodu zarządzanego.|  
|`CODE_INVOKE_KIND_RETURN`|Ta metoda wywoła kodu zarządzanego za pomocą instrukcji return. Przechodzenie krok po kroku, powinien pojawić się w następnym kodu zarządzanego.|  
|`CODE_INVOKE_KIND_TAILCALL`|Ta metoda wywoła kodu zarządzanego za pośrednictwem wywołania tail. Przechodzenie z jednego i Krokowe przechodzenie przez dowolny instrukcje wywołanie powinno pojawić się w kodu zarządzanego.|  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie jest używane przez [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metodę w celu udostępnienia informacji na temat krokowe wykonywanie kodu zarządzanego.  
  
> [!NOTE]
>  To wyliczenie jest przeznaczona do użytku w .NET Native tylko w scenariuszach debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
