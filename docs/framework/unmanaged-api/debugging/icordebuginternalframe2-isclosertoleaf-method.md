---
title: ICorDebugInternalFrame2::IsCloserToLeaf — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
ms.openlocfilehash: 5dd93dcc29ace6573e313f732c45af0dfbb900e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782212"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a>ICorDebugInternalFrame2::IsCloserToLeaf — Metoda
Sprawdza, czy `this` wewnętrzna ramka jest bliżej liścia niż określony obiekt ICorDebugFrame.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFrameToCompare`  
 podczas Wskaźnik do porównania `ICorDebugFrame` obiektu.  
  
 `pIsCloser`  
 [out] `true`, jeśli `this` wewnętrzna ramka jest bliżej liścia niż ramka określona przez `pFrameToCompare`; w przeciwnym razie `false`.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Porównanie zostało wykonane pomyślnie.|  
|E_FAIL|Nie można wykonać porównania.|  
|E_INVALIDARG|`pFrameToCompare` lub `pIsCloser` ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 `IsCloserToLeaf` może służyć do implementowania zasad z przeplotem wewnętrznej ramki z innymi ramkami na stosie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugInternalFrame2, interfejs](icordebuginternalframe2-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
