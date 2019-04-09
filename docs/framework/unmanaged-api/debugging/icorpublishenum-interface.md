---
title: ICorPublishEnum — Interfejs
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1eac0b9fe252e476f8ff781f2181a203886d3beb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160139"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum — Interfejs
Służy jako abstrakcyjny interfejs podstawowy dla wyliczenia, które są używane w publikowanie informacji o procesach i domen aplikacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|Tworzy kopię `ICorPublishEnum` obiektu.|  
|[GetCount, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|Pobiera liczbę elementów w wyliczeniu.|  
|[Reset, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|Przenosi kursora na początku tego wyliczenia.|  
|[Skip, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|Przesuwa kursor do przodu w wyliczeniu przez określoną liczbę elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Następujące moduły wyliczające pochodzić od `ICorPublishEnum`:  
  
-   [Icorpublishappdomainenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CorpubPublish — Klasa coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
