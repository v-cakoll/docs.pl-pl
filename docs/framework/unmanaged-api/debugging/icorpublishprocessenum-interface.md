---
title: ICorPublishProcessEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 3a7267548a957d403cfe02aa3d800a410c14b82a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103420"
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum — Interfejs
Podklasa interfejsu [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) , która dostarcza metody umożliwiające przechodzenie kolekcji obiektów [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|Pobiera określoną liczbę wystąpień `ICorPublishProcess` z kolekcji, rozpoczynając od bieżącego położenia.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorPublishProcessEnum` implementuje metody interfejsu abstrakcyjnego, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).  
  
 Wystąpienie `ICorPublishProcessEnum` jest tworzone przez metodę [ICorPublish:: EnumProcesses —](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) . Przechodzenie kolekcji obiektów `ICorPublishProcess` jest oparte na kryteriach filtrowania określonych w momencie utworzenia wystąpienia `ICorPublishProcessEnum`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [CorpubPublish, klasa coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
