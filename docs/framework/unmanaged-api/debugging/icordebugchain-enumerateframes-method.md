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
ms.openlocfilehash: fc647805fcb7d8354a2540ac9424dc7155853444
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745035"
---
# <a name="icordebugchainenumerateframes-method"></a>ICorDebugChain::EnumerateFrames — Metoda
Pobiera moduł wyliczający, który zawiera wszystkie ramki stosu zarządzanych w łańcuchu, począwszy od najbardziej aktualną ramki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
