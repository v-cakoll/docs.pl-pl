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
ms.openlocfilehash: c4a24d879ebd9e8813ea0ac4597818569f4ae6fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790730"
---
# <a name="icorpublish-interface"></a>ICorPublish — Interfejs
Służy jako ogólny interfejs publikowania informacji o procesach i informacjach o domenach aplikacji w tych procesach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumProcesses, metoda](icorpublish-enumprocesses-method.md)|Pobiera wystąpienie [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) , które zawiera zarządzane procesy uruchomione na tym komputerze.|  
|[GetProcess, metoda](icorpublish-getprocess-method.md)|Pobiera wystąpienie [ICorPublishProcess](icorpublishprocess-interface.md) , które reprezentuje proces o określonym identyfikatorze.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [CorpubPublish, klasa coclass](corpubpublish-coclass.md)
