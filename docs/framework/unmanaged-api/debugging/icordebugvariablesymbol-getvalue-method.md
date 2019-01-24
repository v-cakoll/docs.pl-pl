---
title: Metoda ICorDebugVariableSymbol::GetValue
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14412c11010b94fdc462c5aa29e9bc769b2633cc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496757"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>Metoda ICorDebugVariableSymbol::GetValue
Pobiera wartość zmiennej w postaci tablicy bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `offset`  
 [in] Początkowe przesunięcie w zmiennej, z którego ma zostać odczytana wartość. Ten parametr jest używany podczas odczytywania pola elementu członkowskiego w obiekcie.  
  
 `cbContext`  
 [in] Rozmiar w bajtach `context` argumentu.  
  
 `context`  
 [in] Kontekst wątku, używane do odczytywania wartości.  
  
 `cbValue`  
 [in] Rozmiar w bajtach `pValue` buforu.  
  
 `pcbValue`  
 [out] Liczba bajtów rzeczywiście zapisanych na `pValue` buforu.  
  
 `pValue`  
 [out] Tablica bajtów, która zawiera wartość zmiennej.  
  
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
