---
title: "ICorDebugEval2::NewStringWithLength — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewStringWithLength
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b794482e491dc9825b0311cf1731d159082bd1f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2newstringwithlength-method"></a>ICorDebugEval2::NewStringWithLength — Metoda
Tworzy ciąg o określonej długości, przy użyciu określonej zawartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `string`  
 [in] Wskaźnik do wartości ciągu.  
  
 `uiLength`  
 [in] Długość ciągu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ciąg na końcu znak null powinien być w ciągu zarządzany element wywołujący `NewStringWithLength` metody musi zapewnić, że długość ciągu zawiera znak końcowy null.  
  
 Ciąg zawsze jest tworzony w domenie aplikacji, w którym wątek jest aktualnie wykonywany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
