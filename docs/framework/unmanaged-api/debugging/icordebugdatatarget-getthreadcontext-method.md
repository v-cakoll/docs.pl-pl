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
ms.openlocfilehash: 79708aa5a2abcb8d7465f82a8beb918484c193b9
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976554"
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
 Na platformach Windows `pContext` musi być `CONTEXT` strukturą (zdefiniowaną w Winnt. h), która jest odpowiednia dla typu maszyny określonego przez metodę [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) . `contextFlags`musi mieć te same wartości co `ContextFlags` pole `CONTEXT` struktury. `CONTEXT` Struktura jest specyficzna dla procesora; Szczegóły można znaleźć w pliku WinNT. h.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugDataTarget — Interfejs](icordebugdatatarget-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
