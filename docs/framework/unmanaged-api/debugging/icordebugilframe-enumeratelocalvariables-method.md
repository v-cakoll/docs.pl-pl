---
title: ICorDebugILFrame::EnumerateLocalVariables — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
ms.openlocfilehash: 07331a512dd513a94a7d8c3a8d8b0754d998b94b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131000"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>ICorDebugILFrame::EnumerateLocalVariables — Metoda
Pobiera moduł wyliczający dla zmiennych lokalnych w tej ramce.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppValueEnum`  
 określoną Wskaźnik do adresu obiektu ICorDebugValueEnum, który jest modułem wyliczającym dla zmiennych lokalnych w tej ramce.  
  
## <a name="remarks"></a>Uwagi  
 `EnumerateLocalVariables` Pobiera moduł wyliczający, który może wyświetlić listę zmiennych lokalnych dostępnych w ramce wywołania, która jest reprezentowana przez ten obiekt ICorDebugILFrame. Lista nie może zawierać wszystkich zmiennych lokalnych w uruchomionej funkcji, ponieważ niektóre z nich mogą nie być aktywne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
