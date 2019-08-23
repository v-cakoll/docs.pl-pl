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
ms.openlocfilehash: 6fa8de1a561e59e00d5bd9e78172d78b417aeff0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951964"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>Wyliczenie CorDebugCodeInvokeKind
Opisuje sposób, w jaki wyeksportowana funkcja wywołuje kod zarządzany.  
  
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
|`CODE_INVOKE_KIND_NONE`|Jeśli jakikolwiek kod zarządzany jest wywoływany przez tę metodę, będzie musiał znajdować się w nim jawne zdarzenia lub punkty przerwania.<br /><br /> --lub--<br /><br /> Możemy po prostu zrezygnować z kodu zarządzanego ta metoda wywołuje, ponieważ nie ma prostego sposobu na jej zatrzymanie.<br /><br /> --lub--<br /><br /> Metoda może nigdy nie wywołać kodu zarządzanego.|  
|`CODE_INVOKE_KIND_RETURN`|Ta metoda wywoła kod zarządzany za pośrednictwem instrukcji return. Należy wzważyć przy następnym zarządzanym kodzie.|  
|`CODE_INVOKE_KIND_TAILCALL`|Ta metoda wywoła kod zarządzany za pośrednictwem wywołania tail. Wykonywanie pojedynczych instrukcji wywołania i przechodzenie do nich powinno dotrzeć do kodu zarządzanego.|  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie jest używane przez metodę [Metoda ICorDebugProcess6:: GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) w celu uzyskania informacji na temat wykonywania kroków w kodzie zarządzanym.  
  
> [!NOTE]
> To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
