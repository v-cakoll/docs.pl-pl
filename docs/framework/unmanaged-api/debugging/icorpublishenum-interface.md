---
title: "ICorPublishEnum — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9f09d0f80eba86d03d0db7af8fd63d2231c9a88d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum — Interfejs
Pełni rolę abstrakcyjnej interfejs podstawowy dla wyliczenia, które są używane w publikowaniu informacji o procesach i domen aplikacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|Tworzy kopię tego `ICorPublishEnum` obiektu.|  
|[GetCount, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|Pobiera liczbę elementów w wyliczeniu.|  
|[Reset, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|Przesuwa kursor na początku wyliczenia.|  
|[Skip, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|Przesuwa kursor do przodu w wyliczeniu określoną liczbę elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Następujące moduły wyliczające pochodzi od `ICorPublishEnum`:  
  
-   [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [CorpubPublish, klasa coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
