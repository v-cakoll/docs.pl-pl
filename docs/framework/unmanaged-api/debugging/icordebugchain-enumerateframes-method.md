---
title: "ICorDebugChain::EnumerateFrames — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.EnumerateFrames
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 87e2fbc0a4ca9d97ac7e57234383ebd8cee56211
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchainenumerateframes-method"></a>ICorDebugChain::EnumerateFrames — Metoda
Pobiera moduł wyliczający, który zawiera wszystkie ramki stosu zarządzanych w łańcuchu, zaczynając od ostatniego ramki.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppFrames`  
 [out] Wskaźnik do adresu ICorDebugFrameEnum obiektu, który moduł wyliczający dla ramki stosu.  
  
## <a name="remarks"></a>Uwagi  
 Łańcuch reprezentuje stosu wywołań fizycznych wątku.  
  
 `EnumerateFrames` Metoda powinna być wywoływana tylko do łańcuchów zarządzanych. Interfejsu API debugowania nie udostępnia metody uzyskania ramki zawarte w łańcuchy niezarządzane. Aby uzyskać te informacje debugera należy użyć inny sposób.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
