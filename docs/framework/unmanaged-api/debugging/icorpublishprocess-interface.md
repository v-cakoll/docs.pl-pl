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
ms.openlocfilehash: 19f76a163fae4a1390a2e0fcb85299f8ce78180c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435893"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess — Interfejs
Udostępnia metody, które uzyskują dostęp do informacji wyświetlanych dotyczące procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumAppDomains, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|Pobiera [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) wystąpienia, które zawiera domeny aplikacji w procesie odwołuje się to `ICorPublishProcess`.|  
|[GetDisplayName, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|Pobiera pełną ścieżkę do pliku wykonywalnego procesu, który odwołuje się ten `ICorPublishProcess`.|  
|[GetProcessID, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|Pobiera identyfikator system operacyjny dla procesu, który odwołuje się to `ICorPublishProcess`.|  
|[IsManaged, metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|Pobiera wartość wskazującą, czy proces odwołuje się ten `ICorPublishProcess` wiadomo, że jest uruchomiona kodu zarządzanego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [CorpubPublish, klasa coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
