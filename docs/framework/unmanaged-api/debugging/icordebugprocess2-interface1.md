---
title: ICorDebugProcess2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2
helpviewer_keywords: ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80f6c35ba2ef2ec74293d0f025ddf20254f504a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2-interface1"></a>ICorDebugProcess2 Interface1
Logiczne rozszerzenie ICorDebugProcess — interfejs, który reprezentuje proces uruchamiania kodu zarządzanego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|Usunięcie punktu przerwania od wskazanego przesunięcia, który został ustawiony przez wywołanie wcześniejszych `ICorDebugProcess2::SetUnmanagedBreakpoint`.|  
|[GetDesiredNGENCompilerFlags, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|Pobiera flagi, które muszą być ustawione dla środowisko uruchomieniowe języka wspólnego (CLR) można załadować obrazu z procesem odwołuje się to `ICorDebugProcess2`.|  
|[GetReferenceValueFromGCHandle, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|Pobiera wskaźnik odwołanie do określonego zarządzanego obiektu, który ma obsługiwać wyrzucania elementów bezużytecznych.|  
|[GetThreadForTaskID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|Pobiera wątku, na którym jest wykonywane zadanie o podanym identyfikatorze.|  
|[GetVersion, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|Pobiera wersję środowiska CLR, na którym jest uruchomiona debugowanego procesu.|  
|[SetDesiredNGENCompilerFlags, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|Ustawia flagi, które są wymagane dla kompilatora just in time (JIT) można załadować obrazu w debugowanym procesie.|  
|[SetUnmanagedBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|Ustawia niezarządzanego punktu przerwania w przesunięciu określonego obrazu macierzystego.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
