---
title: ICorDebugVariableSymbol::GetValue — metoda
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5916b1bd89c4f86d76ef4b61afa211b76be94928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422750"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>ICorDebugVariableSymbol::GetValue — metoda
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
 [in] Początkowe przesunięcie w zmiennej, z którego można odczytać wartości. Ten parametr jest używany podczas odczytywania elementu członkowskiego pola obiektu.  
  
 `cbContext`  
 [in] Wyrażony w bajtach rozmiar `context` argumentu.  
  
 `context`  
 [in] Kontekst wątku używany do odczytu wartości.  
  
 `cbValue`  
 [in] Wyrażony w bajtach rozmiar `pValue` buforu.  
  
 `pcbValue`  
 [out] Liczba bajtów zapisywanych faktycznie `pValue` buforu.  
  
 `pValue`  
 [out] Tablica bajtów zawierająca wartość zmiennej.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugVariableSymbol, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
