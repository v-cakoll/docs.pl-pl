---
title: "ICorDebugModule::EnableJITDebugging — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableJITDebugging
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 31fc3b7c2b977dbfd6f10cc767f81748243dfce4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging — Metoda
Określa, czy przy użyciu kompilatora just in time (JIT) zachowuje informacji debugowania dla metod w ramach tego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bTrackJITInfo`  
 [in] Ta wartość `true` umożliwiające kompilatora JIT zachować informacje dotyczące mapowania między wersji języka pośredniego (MSIL) firmy Microsoft i wersji kompilacji JIT każdej metody w tym module.  
  
 `bAllowJitOpts`  
 [in] Ta wartość `true` umożliwia generowanie kodu z niektórych optymalizacje JIT specyficzne dla debugowania przy użyciu kompilatora JIT.  
  
## <a name="remarks"></a>Uwagi  
 Debugowanie JIT jest włączone domyślnie dla wszystkich modułów, które są ładowane, gdy debuger jest aktywny. Programowo włączenie lub wyłączenie ustawienia zastępują ustawienia globalne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
