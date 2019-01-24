---
title: ICorDebugVariableSymbol::SetValue Method
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 427c885dc1d7cbf535656a7db3f40da28c55a9b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630775"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>ICorDebugVariableSymbol::SetValue Method
Wartość tablicy bajtowej jest przypisywany do zmiennej.  
  
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
 [in] Początkowe przesunięcie w zmiennej, w którym można ustawić wartości. Ten parametr jest używany podczas zapisywania do pola elementu członkowskiego w obiekcie.  
  
 `threadID`  
 [in] Identyfikator wątku wątku, którego kontekst muszą zostać zaktualizowane w celu odzwierciedlenia nowej wartości.  
  
 `cbContext`  
 [in] Rozmiar w bajtach kontekst wątku.  
  
 `context`  
 [in] Kontekst wątku, używany do zapisywania wartości.  
  
 `cbValue`  
 [in] Rozmiar w bajtach `pValue` buforu.  
  
 `pValue`  
 [in] Bufor, który zawiera wartość do ustawienia.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugVariableSymbol, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
