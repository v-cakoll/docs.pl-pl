---
title: ICorDebugNativeFrame::SetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: 1d978cab0817af68356d95d635f8d2bfa3fd546a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096741"
---
# <a name="icordebugnativeframesetip-method"></a>ICorDebugNativeFrame::SetIP — Metoda
Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nOffset`  
 podczas Lokalizacja przesunięcia w kodzie natywnym.  
  
## <a name="remarks"></a>Uwagi  
 Wywołania do `SetIP` natychmiast unieważnią wszystkie ramki i łańcuchy dla bieżącego wątku. Jeśli debuger potrzebuje informacji o klatce po wywołaniu do `SetIP`, musi wykonać nowy ślad stosu.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) spróbuje zachować prawidłowy stan ramki stosu. Jednak nawet jeśli ramka jest w prawidłowym stanie, o ile jest to związane ze środowiskiem uruchomieniowym, nadal mogą wystąpić problemy, takie jak Niezainicjowane zmienne lokalne itd. Obiekt wywołujący jest odpowiedzialny za ubezpieczenie spójność uruchomionego programu.  
  
 Na platformach 64-bitowych wskaźnik instrukcji nie może zostać przeniesiony z bloku `catch` lub `finally`. Jeśli `SetIP` jest wywoływana w celu przechodzenia na platformę 64-bitową, zwróci wynik HRESULT wskazujący błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
