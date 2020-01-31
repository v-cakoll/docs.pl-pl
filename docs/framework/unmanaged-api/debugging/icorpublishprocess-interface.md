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
ms.openlocfilehash: 3ae48df9e66890161c1aef944d37b0a279939d56
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790542"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess — Interfejs
Dostarcza metody, które mają dostęp do informacji o procesie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumAppDomains, metoda](icorpublishprocess-enumappdomains-method.md)|Pobiera wystąpienie [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) , które zawiera domeny aplikacji w procesie, do którego odwołuje się ten `ICorPublishProcess`.|  
|[GetDisplayName, metoda](icorpublishprocess-getdisplayname-method.md)|Pobiera pełną ścieżkę pliku wykonywalnego dla procesu, do którego odwołuje się ten `ICorPublishProcess`.|  
|[GetProcessID, metoda](icorpublishprocess-getprocessid-method.md)|Pobiera identyfikator systemu operacyjnego dla procesu, do którego odwołuje się ten `ICorPublishProcess`.|  
|[IsManaged, metoda](icorpublishprocess-ismanaged-method.md)|Pobiera wartość wskazującą, czy proces, do którego odwołuje się ten `ICorPublishProcess`, jest znany jako uruchomiony kod zarządzany.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [CorpubPublish, klasa coclass](corpubpublish-coclass.md)
