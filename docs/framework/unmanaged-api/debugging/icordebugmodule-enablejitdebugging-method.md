---
title: ICorDebugModule::EnableJITDebugging — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
ms.openlocfilehash: bdf027f94c8416d052cb807d04be76a39868ccf7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212935"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging — Metoda
Określa, czy kompilator just in Time (JIT) zachowuje informacje debugowania dla metod w ramach tego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bTrackJITInfo`  
 podczas Ustaw tę wartość, aby `true` umożliwić kompilatorowi JIT zachowywanie informacji o mapowaniu między wersją języka pośredniego firmy Microsoft (MSIL) i skompilowanej przez JIT wersji każdej metody w tym module.  
  
 `bAllowJitOpts`  
 podczas Ustaw tę wartość, aby `true` umożliwić kompilatorowi JIT generowanie kodu z określonymi optymalizacjami specyficznymi dla JIT dla debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Debugowanie JIT jest domyślnie włączone dla wszystkich modułów, które są ładowane, gdy debuger jest aktywny. Programowe Włączanie lub wyłączanie ustawień przesłania ustawienia globalne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
