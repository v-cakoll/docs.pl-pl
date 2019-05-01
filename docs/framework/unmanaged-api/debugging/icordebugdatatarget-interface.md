---
title: ICorDebugDataTarget — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 480fc27bd41f7ca559ceee379b7f6f81c94da0ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989199"
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget — Interfejs
Dostarcza interfejs wywołania zwrotnego, który zapewnia dostęp do konkretnego procesu docelowego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPlatform, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|Zawiera informacje dotyczące platformy, w tym architektury procesora i systemu operacyjnego, na którym jest uruchomiony proces docelowy.|  
|[ReadVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|Pobiera blok pamięci ciągłej uruchamianie pod podanym adresem i zwraca go w dostarczony bufor.|  
|[GetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|Żąda bieżący kontekst wątku określonego wątku.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugDataTarget` i jego metody mają następującą charakterystykę:  
  
- Debugowanie usług wywoływać metody, w tym interfejsie dostępu do pamięci i innych danych w procesie docelowym.  
  
- Klient debugera musi implementować ten interfejs stosownie do określonego celu (na przykład żywy proces lub zrzutu pamięci).  
  
- `ICorDebugDataTarget` Metody może być wywołana tylko z w ramach metod zaimplementowanych w innych `ICorDebug*` interfejsów. Daje to gwarancję, że klient debugera ma kontroluje, przez który wątek jest wywoływana na i.  
  
- `ICorDebugDataTarget` Implementacji zwracana zawsze aktualne informacje dotyczące obiektu docelowego.  
  
 Proces docelowy powinien być zatrzymana i nie uległy zmianie w jakikolwiek sposób podczas `ICorDebug*` interfejsów (i w związku z tym `ICorDebugDataTarget` metody) jest wywoływana. Jeśli obiektem docelowym są żywy proces i zmiany jego stanu, [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metoda musi zostać ponownie wywoływana w celu zapewnienia wystąpienia icordebugprocess — zastąpienie.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
