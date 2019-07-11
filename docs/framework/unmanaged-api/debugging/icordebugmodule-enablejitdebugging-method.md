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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aeb6ed448539db2720fee0d42cfcc344fd3bbf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762763"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging — Metoda
Określa, czy kompilator just-in-time (JIT), zachowuje informacje o debugowaniu dla metod, w tym module.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bTrackJITInfo`  
 [in] Ustaw tę wartość na `true` umożliwiające kompilator JIT, aby zachować informacje dotyczące mapowania między wersji języka intermediate language (MSIL) firmy Microsoft i wersję kompilowanego dokładnie na czas każdej metody w tym module.  
  
 `bAllowJitOpts`  
 [in] Ustaw tę wartość na `true` umożliwiające kompilator JIT wygenerować kod z niektóre optymalizacje JIT specyficzne dla debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Debugowanie JIT jest domyślnie włączone dla wszystkich modułów, które są ładowane, gdy debuger jest aktywny. Programowe Włączanie lub wyłączanie ustawień zastępuje ustawienia globalne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
