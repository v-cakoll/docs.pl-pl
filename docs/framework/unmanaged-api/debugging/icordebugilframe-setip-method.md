---
title: ICorDebugILFrame::SetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 60273d7cf91be04c5fc3041260e4bb146ce9a45e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095429"
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP — Metoda
Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie języka pośredniego firmy Microsoft (MSIL).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nOffset`  
 Lokalizacja przesunięcia w kodzie MSIL.  
  
## <a name="remarks"></a>Uwagi  
 Wywołania do `SetIP` natychmiast unieważnią wszystkie ramki i łańcuchy dla bieżącego wątku. Jeśli debuger potrzebuje informacji o klatce po wywołaniu do `SetIP`, musi wykonać nowy ślad stosu.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) spróbuje zachować prawidłowy stan ramki stosu. Jednak nawet jeśli ramka jest w prawidłowym stanie, nadal mogą wystąpić problemy, takie jak Niezainicjowane zmienne lokalne. Obiekt wywołujący jest odpowiedzialny za zapewnienie spójność uruchomionego programu.  
  
 Na platformach 64-bitowych wskaźnik instrukcji nie może zostać przeniesiony z bloku `catch` lub `finally`. Jeśli `SetIP` jest wywoływana w celu przechodzenia na platformę 64-bitową, zwróci wynik HRESULT wskazujący błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
