---
title: ICorDebugILFrame::EnumerateArguments — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
ms.openlocfilehash: d74c5a6f966201c8ca9d2854de2e9986e7f1d0fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131031"
---
# <a name="icordebugilframeenumeratearguments-method"></a>ICorDebugILFrame::EnumerateArguments — Metoda
Pobiera moduł wyliczający dla argumentów w tej ramce.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppValueEnum`  
 określoną Wskaźnik do adresu obiektu ICorDebugValueEnum, który jest modułem wyliczającym dla argumentów w tej ramce.  
  
## <a name="remarks"></a>Uwagi  
 `EnumerateArguments` Pobiera moduł wyliczający, który może wyświetlać listę argumentów dostępnych w ramce wywołania, która jest reprezentowana przez ten obiekt ICorDebugILFrame. Lista będzie zawierać argumenty, które są [vararg](/cpp/windows/vararg) (czyli zmienną liczbę argumentów), a także argumenty, które nie są `vararg`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
