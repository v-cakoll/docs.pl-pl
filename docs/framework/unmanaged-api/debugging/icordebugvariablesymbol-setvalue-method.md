---
title: 'ICorDebugVariableSymbol:: SetValue — Metoda'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: 38afd355938ec1beb1dbfd33de36116d25b07b4e
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397078"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>ICorDebugVariableSymbol:: SetValue — Metoda
Przypisuje wartość tablicy bajtów do zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `offset`  
 podczas Przesunięcie początkowe w zmiennej, w której ma zostać ustawiona wartość. Ten parametr jest używany podczas zapisywania do pól elementu członkowskiego w obiekcie.  
  
 `threadID`  
 podczas Identyfikator wątku, którego kontekst musi zostać zaktualizowany w celu odzwierciedlenia nowej wartości.  
  
 `cbContext`  
 podczas Rozmiar w bajtach kontekstu wątku.  
  
 `context`  
 podczas Kontekst wątku używany do zapisania wartości.  
  
 `cbValue`  
 podczas Rozmiar w bajtach `pValue` buforu.  
  
 `pValue`  
 podczas Bufor, który zawiera wartość do ustawienia.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugVariableSymbol, interfejs](icordebugvariablesymbol-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
