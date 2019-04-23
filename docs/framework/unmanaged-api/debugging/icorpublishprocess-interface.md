---
title: ICorPublishProcess — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08dfa3ddbfd9cffdb0cb88d0325e5703a854668a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182965"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess — Interfejs
Udostępnia metody, uzyskujących dostęp do informacji wyświetlanych informacji na temat procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumAppDomains, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|Pobiera [icorpublishappdomainenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) wystąpienia, które zawiera domen aplikacji w procesie przywoływane przez to `ICorPublishProcess`.|  
|[GetDisplayName, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|Pobiera pełną ścieżkę pliku wykonywalnego procesu odwołuje się ten `ICorPublishProcess`.|  
|[GetProcessID, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|Pobiera identyfikator systemu operacyjnego dla procesu, który odwołuje się ten `ICorPublishProcess`.|  
|[IsManaged, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|Pobiera wartość wskazującą, czy proces odwołuje się ten `ICorPublishProcess` jest znany uruchomienia kodu zarządzanego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [CorpubPublish, klasa coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
