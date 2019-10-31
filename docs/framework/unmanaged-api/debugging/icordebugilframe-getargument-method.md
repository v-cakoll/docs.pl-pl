---
title: ICorDebugILFrame::GetArgument — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
ms.openlocfilehash: 01c7cb2e4359a477c26f995602dbf29668e567c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131021"
---
# <a name="icordebugilframegetargument-method"></a>ICorDebugILFrame::GetArgument — Metoda
Pobiera wartość określonego argumentu w ramce stosu języka pośredniego (MSIL) firmy Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwIndex`  
 podczas Indeks argumentu w tej ramce stosu MSIL.  
  
 `ppValue`  
 określoną Wskaźnik do adresu obiektu ICorDebugValue, który reprezentuje pobraną wartość.  
  
## <a name="remarks"></a>Uwagi  
 Metody `GetArgument` można użyć w ramce stosu MSIL lub w ramce skompilowanej just-in-Time (JIT).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
