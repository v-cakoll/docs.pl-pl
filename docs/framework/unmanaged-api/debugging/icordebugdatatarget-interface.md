---
title: "ICorDebugDataTarget — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget
helpviewer_keywords: ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5d3a3b190cfa606bd4239e24c5defdaff9f4257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget — Interfejs
Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPlatform, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|Zawiera informacje o platformie, w tym architektury procesora i systemu operacyjnego, na którym jest uruchomiony proces docelowy.|  
|[ReadVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|Pobiera blok pamięci ciągłej, zaczynając od określonego adresu i zwraca go do dostarczonego buforu.|  
|[GetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|Żąda bieżący kontekst wątku określonego wątku.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugDataTarget`i jego metody mają następujące cechy:  
  
-   Debugowanie usług wywoływać metod w tym interfejsie dostęp do pamięci i innych danych w procesie docelowym.  
  
-   Klient debugera musi implementować ten interfejs na potrzeby określonego elementu docelowego (na przykład procesu na żywo lub zrzut pamięci).  
  
-   `ICorDebugDataTarget` Metody można wywołać tylko z wewnątrz metody implementowane w innych `ICorDebug*` interfejsów. Dzięki temu klient debugera ma kontroli, przez który wątek jest wywoływana na i.  
  
-   `ICorDebugDataTarget` Implementacji zawsze musi zwracać aktualnych informacji dotyczących obiektu docelowego.  
  
 Proces docelowy powinien zatrzymana i nie uległy zmianie w jakikolwiek sposób podczas `ICorDebug*` interfejsów (i w związku z tym `ICorDebugDataTarget` metody) są wywoływane. Jeśli obiektem docelowym jest procesem na żywo i jego zmiany stanu [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metoda musi ponownie wywołany, aby zapewnić wystąpienie ICorDebugProcess zastąpienia.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
