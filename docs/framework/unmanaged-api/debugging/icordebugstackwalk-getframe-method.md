---
title: ICorDebugStackWalk::GetFrame — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: 77210edfdc954f38ff06bc43a8b41a6abe8dc3d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131838"
---
# <a name="icordebugstackwalkgetframe-method"></a>ICorDebugStackWalk::GetFrame — Metoda
Pobiera bieżącą ramkę w obiekcie [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFrame`  
 podczas Wskaźnik do adresu utworzonego obiektu Frame, który reprezentuje bieżącą ramkę w stosie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Środowisko uruchomieniowe pomyślnie zwróciło bieżącą ramkę.|  
|E_FAIL|Bieżąca ramka nie została zwrócona.|  
|S_FALSE|Bieżąca ramka jest natywną ramką stosu.|  
|E_INVALIDARG|`pFrame` ma wartość null.|  
|CORDBG_E_PAST_END_OF_STACK|Wskaźnik ramki znajduje się już na końcu stosu; w związku z tym nie można uzyskać dostępu do dodatkowych ramek.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugStackWalk` zwraca tylko rzeczywiste ramki stosu. Użyj metody [ICorDebugThread3:: GetActiveInternalFrames —](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) , aby zwrócić ramki wewnętrzne. (Ramki wewnętrzne to struktury danych wypychane na stosie przez środowisko uruchomieniowe do przechowywania danych tymczasowych).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugStackWalk, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
