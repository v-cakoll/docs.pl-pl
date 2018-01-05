---
title: "IManagedObject::GetObjectIdentity — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IManagedObject.GetObjectIdentity
api_location: mscoree.dll
api_type: COM
f1_keywords: GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c5654865c557e6e004685f66753366d7cb575919
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imanagedobjectgetobjectidentity-method"></a>IManagedObject::GetObjectIdentity — Metoda
Pobiera tożsamość tego zarządzanego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBSTRGUID`  
 [out] Wskaźnik do identyfikatora GUID procesu, w której znajduje się obiekt.  
  
 `AppDomainID`  
 [out] Wskaźnik do identyfikator domeny aplikacji obiektu.  
  
 `pCCW`  
 [out] Wskaźnik do obiektu indeksu w klasycznym modelu COM v-table.  
  
## <a name="remarks"></a>Uwagi  
 Tożsamość obiektu zarządzanego obejmuje proces identyfikator GUID, identyfikator domeny aplikacji i indeks obiektu w klasycznym modelu COM v-table.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IManagedObject, interfejs](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
