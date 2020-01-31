---
title: ICorDebugModule2::GetJITCompilerFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.GetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::GetJITCompilerFlags
helpviewer_keywords:
- GetJITCompilerFlags method [.NET Framework debugging]
- ICorDebugModule2::GetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: 7212d9f4-989b-44e3-b8d4-ffc35922f6a0
topic_type:
- apiref
ms.openlocfilehash: ab6551ba70ed4cd154b166eeb92138b6550d2cb2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792979"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a>ICorDebugModule2::GetJITCompilerFlags — Metoda
Pobiera flagi kontrolujące kompilację just-in-Time (JIT) tej ICorDebugModule2.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwFlags`  
 określoną Wskaźnik do wartości wyliczenia [CorDebugJITCompilerFlags —](cordebugjitcompilerflags-enumeration.md) , która kontroluje kompilację JIT.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
