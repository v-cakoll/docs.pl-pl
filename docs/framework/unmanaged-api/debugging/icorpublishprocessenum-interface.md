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
ms.openlocfilehash: 188ff8feabd704d828256a09aca20f9db2227f2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790508"
---
# <a name="icorpublishprocessenum-interface"></a>ICorPublishProcessEnum — Interfejs
Podklasa interfejsu [ICorPublishEnum](icorpublishenum-interface.md) , która dostarcza metody umożliwiające przechodzenie kolekcji obiektów [ICorPublishProcess](icorpublishprocess-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next, metoda](icorpublishprocessenum-next-method.md)|Pobiera określoną liczbę wystąpień `ICorPublishProcess` z kolekcji, rozpoczynając od bieżącego położenia.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorPublishProcessEnum` implementuje metody interfejsu abstrakcyjnego, [ICorPublishEnum](icorpublishenum-interface.md).  
  
 Wystąpienie `ICorPublishProcessEnum` jest tworzone przez metodę [ICorPublish:: EnumProcesses —](icorpublish-enumprocesses-method.md) . Przechodzenie kolekcji obiektów `ICorPublishProcess` jest oparte na kryteriach filtrowania określonych w momencie utworzenia wystąpienia `ICorPublishProcessEnum`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [CorpubPublish, klasa coclass](corpubpublish-coclass.md)
