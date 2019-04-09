---
title: ICorPublishProcess::EnumAppDomains — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 173a7d6793bec9262efb661d56e3a371d0bf9b47
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164609"
---
# <a name="icorpublishprocessenumappdomains-method"></a>ICorPublishProcess::EnumAppDomains — Metoda
Pobiera moduł wyliczający dla domen aplikacji w procesie, który odwołuje się do niej to [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Wskaźnik na adres [icorpublishappdomainenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) wystąpienia, która umożliwia iteracji przez kolekcję domen aplikacji w ramach tego procesu.  
  
## <a name="remarks"></a>Uwagi  
 Lista domen aplikacji jest oparte na migawkach domen aplikacji, które istnieją podczas `EnumAppDomains` metoda jest wywoływana. Ta metoda może być wywoływana więcej niż raz utworzyć nową listę aktualne. Kolejne wywołania tej metody nie wpłynie istniejące listy.  
  
 Jeśli proces został zakończony, `EnumAppDomains` zakończy się niepowodzeniem z wartością HRESULT w CORDBG_E_PROCESS_TERMINATED.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorPublishProcess — Interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
