---
title: ICorDebugStepper::SetUnmappedStopMask — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0a273c54559e8e297e09740ba9c770ce12d72d1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760585"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask — Metoda
Ustawia wartość, która określa typ niezamapowane kodu, w którym wykonywanie zostanie zatrzymany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mask`  
 [in] Wartość cordebugunmappedstop — wyliczenie, który określa typ niezamapowane kodu, w której debuger będzie zatrzymuje wykonywanie.  
  
 Wartość domyślna to STOP_OTHER_UNMAPPED. Wartość STOP_UNMANAGED tylko jest prawidłowa w przypadku debugowania międzyoperacyjnego.  
  
## <a name="remarks"></a>Uwagi  
 Gdy debuger wykryje just-in-time kompilacji (JIT), który nie ma odpowiedniego mapowania do języka Microsoft intermediate language (MSIL), zatrzymuje wykonywanie, jeśli została ustawiona flaga określania typu niezamapowane kodu; w przeciwnym razie wykonywanie krokowe w sposób niewidoczny dla użytkownika jest kontynuowane.  
  
 Jeśli debuger nie używa stepper wprowadzenie metody, następnie go nie zawsze Przekrocz nad niezamapowane kodu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
