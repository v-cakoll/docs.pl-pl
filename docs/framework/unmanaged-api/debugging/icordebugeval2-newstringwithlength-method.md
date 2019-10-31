---
title: ICorDebugEval2::NewStringWithLength — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: 3836b6c08098d38516c8a25260fb28998a2317fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084785"
---
# <a name="icordebugeval2newstringwithlength-method"></a>ICorDebugEval2::NewStringWithLength — Metoda
Tworzy ciąg o określonej długości z określoną zawartością.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `string`  
 podczas Wskaźnik do wartości ciągu.  
  
 `uiLength`  
 podczas Długość ciągu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli oczekiwany znak null ciągu powinien znajdować się w ciągu zarządzanym, wywołujący metodę `NewStringWithLength` musi mieć pewność, że długość ciągu zawiera końcowy znak null.  
  
 Ten ciąg jest zawsze tworzony w domenie aplikacji, w której jest aktualnie wykonywany wątek.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
