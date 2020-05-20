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
ms.openlocfilehash: 8d958e949612b502ab218f5c6b75779174d34e19
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421088"
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess — Interfejs
Dostarcza metody, które mają dostęp do informacji o procesie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumAppDomains, metoda](icorpublishprocess-enumappdomains-method.md)|Pobiera wystąpienie [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) , które zawiera domeny aplikacji w procesie, do którego się odwołuje `ICorPublishProcess` .|  
|[GetDisplayName — Metoda](icorpublishprocess-getdisplayname-method.md)|Pobiera pełną ścieżkę pliku wykonywalnego dla procesu, do którego się odwołuje `ICorPublishProcess` .|  
|[GetProcessID, metoda](icorpublishprocess-getprocessid-method.md)|Pobiera identyfikator systemu operacyjnego dla procesu, do którego się odwołuje `ICorPublishProcess` .|  
|[IsManaged, metoda](icorpublishprocess-ismanaged-method.md)|Pobiera wartość wskazującą, czy proces, do którego się odwołuje, `ICorPublishProcess` jest znany jako uruchomiony kod zarządzany.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [CorpubPublish — Klasa coclass](corpubpublish-coclass.md)
