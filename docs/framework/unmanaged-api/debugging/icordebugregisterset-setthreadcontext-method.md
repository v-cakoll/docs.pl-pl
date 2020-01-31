---
title: ICorDebugRegisterSet::SetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
ms.openlocfilehash: dc2a41524d3fafe1cb45c9494d80aabe7dae0ed8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792040"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a>ICorDebugRegisterSet::SetThreadContext — Metoda
`SetThreadContext` nie została zaimplementowana w .NET Framework wersji 2,0. Nie wywołuj tej metody.  
  
> [!NOTE]
> Użyj operacji wyższego poziomu [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) , aby ustawić kontekst wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 1,1, 1,0  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRegisterSet, interfejs](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2, interfejs](icordebugregisterset2-interface.md)
