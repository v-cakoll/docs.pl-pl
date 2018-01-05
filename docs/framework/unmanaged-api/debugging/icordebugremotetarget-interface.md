---
title: "ICorDebugRemoteTarget — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget
helpviewer_keywords: ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcfdab2857745dee7c40823ad25592de5dc833ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotetarget-interface"></a>ICorDebugRemoteTarget — Interfejs
Udostępnia metody, które umożliwiają deweloperom debugowanie aplikacji Silverlight w wspólnego języka środowiska środowiska uruchomieniowego (języka wspólnego CLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ICorDebugRemoteTarget::GetHostName, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|Zwraca nazwę hosta lub adres IP komputera zdalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Debugowanie w trybie mieszanym (to znaczy kodu zarządzanego i natywnego) nie jest obsługiwana w systemie Windows 95, Windows 98 lub Windows ME ani na platformach innych niż x86 (na przykład IA-64 i AMD64).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl  
  
 **Biblioteka:** : CorGuids.lib  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugRemote, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
