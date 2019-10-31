---
title: 'ICorDebugVariableSymbol:: GetValue — Metoda'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: 5ef7e67efb2bafd9b9f52203246fd7d1590e6107
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120965"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>ICorDebugVariableSymbol:: GetValue — Metoda
Pobiera wartość zmiennej jako tablicę bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `offset`  
 podczas Przesunięcie początkowe w zmiennej, z której ma zostać odczytana wartość. Ten parametr jest używany podczas odczytywania pól elementu członkowskiego w obiekcie.  
  
 `cbContext`  
 podczas Rozmiar w bajtach argumentu `context`.  
  
 `context`  
 podczas Kontekst wątku używany do odczytywania wartości.  
  
 `cbValue`  
 podczas Rozmiar w bajtach buforu `pValue`.  
  
 `pcbValue`  
 określoną Liczba bajtów rzeczywiście zapisywana w buforze `pValue`.  
  
 `pValue`  
 określoną Tablica bajtów, która zawiera wartość zmiennej.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugVariableSymbol, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
