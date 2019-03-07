---
title: ICorDebugChain::EnumerateFrames — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568f8ca3b92ef465ab595348f68895f389d61e4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489712"
---
# <a name="icordebugchainenumerateframes-method"></a>ICorDebugChain::EnumerateFrames — Metoda
Pobiera moduł wyliczający, który zawiera wszystkie ramki stosu zarządzanych w łańcuchu, począwszy od najbardziej aktualną ramki.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppFrames`  
 [out] Wskaźnik na adres icordebugframeenum — obiekt, który jest moduł wyliczający ramek stosu.  
  
## <a name="remarks"></a>Uwagi  
 Łańcuch reprezentuje stosu wywołań fizycznych dla wątku.  
  
 `EnumerateFrames` Metodę należy wywoływać tylko w przypadku zarządzanych łańcuchów. Interfejsu API debugowania nie udostępnia metody uzyskania ramek, znajdujących się w łańcuchy niezarządzanych. Debuger, należy użyć inny sposób, aby uzyskać te informacje.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
