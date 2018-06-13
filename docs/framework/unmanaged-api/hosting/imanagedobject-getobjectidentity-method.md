---
title: IManagedObject::GetObjectIdentity — Metoda
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1975e5bf20453a3bcd6761d9734be7ddd2ceef7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440330"
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
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IManagedObject, interfejs](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
