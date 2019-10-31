---
title: ICorDebugEval::NewString — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
ms.openlocfilehash: 8a5d421bf0eb8ec5a34fe21d6efc79bbe56c294c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137645"
---
# <a name="icordebugevalnewstring-method"></a>ICorDebugEval::NewString — Metoda
Przydziela nowe wystąpienie ciągu z określoną zawartością.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `string`  
 podczas Wskaźnik do zawartości dla ciągu.  
  
## <a name="remarks"></a>Uwagi  
 Ten ciąg jest zawsze tworzony w domenie aplikacji, w której jest aktualnie wykonywany wątek.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
