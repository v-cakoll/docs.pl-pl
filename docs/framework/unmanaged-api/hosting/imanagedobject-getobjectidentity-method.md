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
ms.openlocfilehash: 8c884569a452fb2985713956f942205cda6ea1ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141247"
---
# <a name="imanagedobjectgetobjectidentity-method"></a>IManagedObject::GetObjectIdentity — Metoda
Pobiera tożsamość tego obiektu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pBSTRGUID`  
 określoną Wskaźnik do identyfikatora GUID procesu, w którym znajduje się obiekt.  
  
 `AppDomainID`  
 określoną Wskaźnik do identyfikatora domeny aplikacji obiektu.  
  
 `pCCW`  
 określoną Wskaźnik do indeksu obiektu w klasycznej tabeli COM.  
  
## <a name="remarks"></a>Uwagi  
 Tożsamość obiektu zarządzanego obejmuje identyfikator GUID procesu, identyfikator domeny aplikacji i indeks obiektu w klasycznej tabeli COM.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IManagedObject, interfejs](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
