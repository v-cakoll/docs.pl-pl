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
ms.openlocfilehash: cf777214c015f0bbc434e3123d3ec7ef7f723549
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405655"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>Wyliczenie CorDebugCodeInvokeKind
W tym artykule opisano, jak wyeksportowanej funkcji wywołuje kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`CODE_INVOKE_KIND_NONE`|Jeśli dowolny kod zarządzany jest wywoływany przez tę metodę, będzie musiał znajdować się później przez jawne zdarzenia lub punktów przerwania.<br /><br /> --lub--<br /><br /> Firma Microsoft może po prostu nie niektóre z kodu zarządzanego, wywołania tej metody, ponieważ nie istnieje łatwy sposób można zatrzymać na nim.<br /><br /> --lub--<br /><br /> Metoda nigdy nie mogą wywoływać kodu zarządzanego.|  
|`CODE_INVOKE_KIND_RETURN`|Ta metoda wywoła kodu zarządzanego za pośrednictwem instrukcji return. Wykonywanie krok po kroku, powinien przyjeździe kolejnego kodu zarządzanego.|  
|`CODE_INVOKE_KIND_TAILCALL`|Ta metoda wywoła kodu zarządzanego za pośrednictwem wywołania tail. Krokowe wykonywanie jednego i pominięcie żadnego wywołania instrukcje powinny przyjeździe kodu zarządzanego.|  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie jest używany przez [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metody, aby podać informacje o krokowe wykonywanie kodu zarządzanego.  
  
> [!NOTE]
>  To wyliczenie jest przeznaczona do użycia w platformę .NET Native tylko w scenariuszach debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
