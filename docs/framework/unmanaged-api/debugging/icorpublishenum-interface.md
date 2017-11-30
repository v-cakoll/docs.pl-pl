---
title: "ICorPublishEnum — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum
helpviewer_keywords: ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7034945824e439b42134f8ea3c13bfaf73dbb649
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum — Interfejs
Pełni rolę abstrakcyjnej interfejs podstawowy dla wyliczenia, które są używane w publikowaniu informacji o procesach i domen aplikacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone — metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|Tworzy kopię tego `ICorPublishEnum` obiektu.|  
|[GetCount — metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|Pobiera liczbę elementów w wyliczeniu.|  
|[Reset — metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|Przesuwa kursor na początku wyliczenia.|  
|[SKIP — metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|Przesuwa kursor do przodu w wyliczeniu określoną liczbę elementów.|  
  
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
 [Corpubpublish — klasa Coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
