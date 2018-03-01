---
title: "ICorDebugStepper::SetUnmappedStopMask — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2fffd523caef6bba1b495f9b8a257f57bd8955af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask — Metoda
Ustawia wartość, która określa typ Niemapowane kodu, w którym zostanie zatrzymanie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mask`  
 [in] Wartość cordebugunmappedstop — wyliczenie, która określa typ Niemapowane kodu, w której debuger będzie zatrzymuje wykonywanie.  
  
 Wartość domyślna to STOP_OTHER_UNMAPPED. Wartość STOP_UNMANAGED jest prawidłowa tylko z debugowania międzyoperacyjnego.  
  
## <a name="remarks"></a>Uwagi  
 Gdy debuger znajduje się w czasie kompilacji (JIT), który nie ma odpowiedniego mapowania na język pośredni firmy Microsoft (MSIL), zatrzymuje wykonywanie, jeśli została ustawiona flaga określenie typu Niemapowane kodu; w przeciwnym razie krok w sposób niewidoczny dla użytkownika jest kontynuowane.  
  
 Jeśli debuger nie używa stepper wprowadzenia metody, następnie go nie zawsze Przekrocz nad Niemapowane kodu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
