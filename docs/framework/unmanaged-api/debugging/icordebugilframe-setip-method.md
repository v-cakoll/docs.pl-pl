---
title: "ICorDebugILFrame::SetIP — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.SetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b92dc50777d55ba6bfa1a0559ab198dd69114ade
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP — Metoda
Ustawia wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie języka pośredniego (MSIL) firmy Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nOffset`  
 Przesunięcie lokalizacji w kodzie MSIL.  
  
## <a name="remarks"></a>Uwagi  
 Wywołuje się `SetIP` natychmiast unieważnia wszystkie ramki i łańcuchów bieżącego wątku. Jeśli debuger musi ramki informacji po wywołaniu `SetIP`, należy wykonać nowe ślad stosu.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) będzie próbował zachować ramki stosu w prawidłowym stanie. Jednak nawet jeśli ramki jest w nieprawidłowym stanie, nadal mogą istnieć problemów, takich jak niezainicjowanych zmiennych lokalnych. Element wywołujący jest odpowiedzialny za zapewnienie spójności uruchomiony program.  
  
 Na platformach 64-bitowych wskaźnik instrukcji nie można przenieść poza `catch` lub `finally` bloku. Jeśli `SetIP` jest nazywany aby ruch na 64-bitowej platformy, zwróci HRESULT informujący o niepowodzeniu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
