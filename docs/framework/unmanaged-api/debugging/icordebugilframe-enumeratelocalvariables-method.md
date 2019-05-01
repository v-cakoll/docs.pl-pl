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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cc9601105d05740e6db0a41bae521bd9a276d74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988653"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>ICorDebugILFrame::EnumerateLocalVariables — Metoda
Pobiera moduł wyliczający dla zmiennych lokalnych w tej ramce.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppValueEnum`  
 [out] Wskaźnik na adres icordebugvalueenum — obiekt, który jest moduł wyliczający dla zmiennych lokalnych w tej ramce.  
  
## <a name="remarks"></a>Uwagi  
 `EnumerateLocalVariables` Pobiera moduł wyliczający, który można wyświetlić listę zmiennych lokalnych dostępnych w ramce wywołań, który jest reprezentowany przez ten obiekt ICorDebugILFrame. Listy mogą nie uwzględniać całego zmiennych lokalnych w uruchomionej funkcji, ponieważ niektóre z nich nie może być aktywne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
