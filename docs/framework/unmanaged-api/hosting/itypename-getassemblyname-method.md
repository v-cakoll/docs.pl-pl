---
title: ITypeName::GetAssemblyName — Metoda
ms.date: 03/30/2017
api_name:
- ITypeName.GetAssemblyName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetAssemblyName
helpviewer_keywords:
- ITypeName::GetAssemblyName method [.NET Framework hosting]
- GetAssemblyName method [.NET Framework hosting]
ms.assetid: 97801d99-f5f1-4a30-882f-959827093fac
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b983491c3794603bea250e684ee097397aa004a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440177"
---
# <a name="itypenamegetassemblyname-method"></a>ITypeName::GetAssemblyName — Metoda
Ta metoda obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
