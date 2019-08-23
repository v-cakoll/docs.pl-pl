---
title: ICorDebugModule2, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8fe1a25c4bc1f5e19f49f0d660d0aad5a180ea2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911886"
---
# <a name="icordebugmodule2-interface"></a>ICorDebugModule2, interfejs

Służy jako logiczne rozszerzenie interfejsu ICorDebugModule.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ApplyChanges, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|Stosuje zmiany w metadanych i zmiany w kodzie języka pośredniego firmy Microsoft (MSIL) do uruchomionego procesu.|  
|[GetJITCompilerFlags, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|Pobiera flagi kontrolujące kompilację just-in-Time (JIT) dla tego `ICorDebugModule2`elementu.|  
|[ResolveAssembly, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|Rozwiązuje zestaw, do którego odwołuje się określony token metadanych.|  
|[SetJITCompilerFlags, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|Ustawia flagi kontrolujące kompilację JIT dla tego `ICorDebugModule2`elementu.|  
|[SetJMCStatus, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|Ustawia stan tylko mój kod (JMC) dla wszystkich metod wszystkich klas w tym `ICorDebugModule2` celu do określonej wartości, z wyjątkiem tych `pTokens` w tablicy, które są ustawiane na wartość odwrotną.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
