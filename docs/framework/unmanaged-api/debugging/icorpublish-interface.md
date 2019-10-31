---
title: ICorPublish — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: 70cf2d76c7c5d1c3431506685f8506e44ab9ec4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121765"
---
# <a name="icorpublish-interface"></a>ICorPublish — Interfejs
Służy jako ogólny interfejs publikowania informacji o procesach i informacjach o domenach aplikacji w tych procesach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumProcesses, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|Pobiera wystąpienie [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) , które zawiera zarządzane procesy uruchomione na tym komputerze.|  
|[GetProcess, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|Pobiera wystąpienie [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) , które reprezentuje proces o określonym identyfikatorze.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [CorpubPublish, klasa coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
