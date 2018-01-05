---
title: "ICorDebugVariableSymbol::SetValue — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2433274c2b8fa3ac547696c03a0d0e25c8b63082
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>ICorDebugVariableSymbol::SetValue — metoda
Przypisuje wartość tablica bajtów do zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `offset`  
 [in] Początkowe przesunięcie w zmiennej, w którym można ustawić wartości. Ten parametr jest używany podczas zapisywania do elementu członkowskiego pola obiektu.  
  
 `threadID`  
 [in] Identyfikator wątku wątku, którego kontekst muszą zostać zaktualizowane w celu uwzględnienia nowej wartości.  
  
 `cbContext`  
 [in] Rozmiar w bajtach kontekst wątku.  
  
 `context`  
 [in] Kontekst wątku używany do zapisu wartości.  
  
 `cbValue`  
 [in] Wyrażony w bajtach rozmiar `pValue` buforu.  
  
 `pValue`  
 [in] Buforu, który zawiera wartość do ustawienia.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugVariableSymbol, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
