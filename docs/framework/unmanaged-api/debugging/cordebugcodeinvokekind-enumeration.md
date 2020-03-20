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
ms.openlocfilehash: 54332f5b3383f1c1513242a79cbd81eb8aa5c4f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179261"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>Wyliczenie CorDebugCodeInvokeKind
W tym artykule opisano, jak wyeksportowana funkcja wywołuje kod zarządzany.  
  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|Jeśli dowolny kod zarządzany jest wywoływany przez tę metodę, będzie musiał znajdować się przez jawne zdarzenia lub punkty przerwania później.<br /><br /> --lub--<br /><br /> Możemy po prostu pominąć niektóre kod zarządzany tej metody wywołuje, ponieważ nie ma łatwego sposobu, aby zatrzymać się na nim.<br /><br /> --lub--<br /><br /> Metoda nigdy nie może wywołać kod zarządzany.|  
|`CODE_INVOKE_KIND_RETURN`|Ta metoda wywoła kod zarządzany za pomocą instrukcji zwracania. Wychodząc powinien dotrzeć do następnego kodu zarządzanego.|  
|`CODE_INVOKE_KIND_TAILCALL`|Ta metoda będzie wywoływać kod zarządzany za pośrednictwem wywołania ogona. Pojedynczy krok po kroku i przechodzenie przez wszelkie instrukcje wywołania powinny uzyskać kod zarządzany.|  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie jest używane przez [metodę ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) w celu zapewnienia informacji o przechodzeniu przez kod zarządzany.  
  
> [!NOTE]
> To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania natywnego platformy .NET.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie, wyliczenia](debugging-enumerations.md)
- [Debugging](index.md)
