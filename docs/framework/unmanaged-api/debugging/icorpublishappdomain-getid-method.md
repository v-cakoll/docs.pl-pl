---
title: ICorPublishAppDomain::GetID — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a7541a2093fe877fb84a8a05237f18c4da43c44
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465988"
---
# <a name="icorpublishappdomaingetid-method"></a>ICorPublishAppDomain::GetID — Metoda
Pobiera unikatowy identyfikator dla tego [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `puId`  
 [out] Wskaźnik do identyfikatora domeny aplikacji.  
  
## <a name="remarks"></a>Uwagi  
 Identyfikator jest unikatowy tylko w zakresie zawierających procesu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorPublishAppDomain, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
