---
title: ICorDebugNativeFrame2::GetStackParameterSize — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
ms.openlocfilehash: 4dd9760c347bbc23f3e8225c1ff748c6b7b8bfe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096536"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a>ICorDebugNativeFrame2::GetStackParameterSize — Metoda
Zwraca skumulowany rozmiar parametrów na stosie w systemach operacyjnych x86.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a>Parametry  
 `pSize`  
 określoną Wskaźnik do skumulowanego rozmiaru parametrów na stosie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Rozmiar stosu został pomyślnie zwrócony.|  
|S_FALSE|`GetStackParameterSize` został wywołany na platformie innej niż x86.|  
|E_FAIL|`The size of the parameters could not be returned`.,|  
|E_INVALIDARG|`pSize` jest `null`.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Metody [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nie dostosowują wskaźnika stosu dla parametrów, które są wypychane na stosie. Zamiast tego można użyć wartości zwracanej przez `GetStackParameterSize`, aby dostosować Wskaźnik stosu do inicjatora natywnego, który dostosowuje parametry.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugNativeFrame2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
