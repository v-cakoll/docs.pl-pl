---
title: ICorDebugDataTarget::GetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
ms.openlocfilehash: 3eace2d91b3bb6e637a659b8b49a31450ebc2c42
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783730"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>ICorDebugDataTarget::GetThreadContext — Metoda
Zwraca bieżący kontekst wątku dla określonego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwThreadID`  
 podczas Identyfikator wątku, którego kontekst ma zostać pobrany. Identyfikator jest zdefiniowany przez system operacyjny.  
  
 `contextFlags`  
 podczas Bitowa kombinacja flag zależnych od platformy wskazująca, które fragmenty kontekstu mają być odczytywane.  
  
 `contextSize`  
 podczas Rozmiar `pContext`.  
  
 `pContext`  
 określoną Bufor, w którym będzie przechowywany kontekst wątku.  
  
## <a name="remarks"></a>Uwagi  
 Na platformach Windows `pContext` musi być strukturą `CONTEXT` (zdefiniowaną w WinNT. h), która jest odpowiednia dla typu maszyny określonego przez metodę [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) . `contextFlags` muszą mieć te same wartości, co pole `ContextFlags` struktury `CONTEXT`. Struktura `CONTEXT` jest specyficzna dla procesora; Szczegóły można znaleźć w pliku WinNT. h.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDataTarget, interfejs](icordebugdatatarget-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
