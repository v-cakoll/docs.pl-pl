---
title: "ICorPublishProcess::EnumAppDomains — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.EnumAppDomains
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 09d6a75fa5c0562f466dba45707795ef7fd161db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessenumappdomains-method"></a>ICorPublishProcess::EnumAppDomains — Metoda
Pobiera moduł wyliczający dla domeny aplikacji w procesie, który odwołuje się do niego to [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Wskaźnik do adresu [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) wystąpienie, które umożliwia iteracji za pomocą kolekcji domeny aplikacji w tym procesie.  
  
## <a name="remarks"></a>Uwagi  
 Listy domen aplikacji jest oparte na migawkach domen aplikacji, które istnieją podczas `EnumAppDomains` metoda jest wywoływana. Ta metoda może wywołać więcej niż raz w celu utworzenia nowej listy aktualne. Kolejne wywołania tej metody nie będzie mieć wpływ na istniejące listy.  
  
 Jeśli proces został zakończony, `EnumAppDomains` zakończy się niepowodzeniem z wartością HRESULT z CORDBG_E_PROCESS_TERMINATED.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorPublishProcess — interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
