---
title: ICLRStrongName2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf9e3d2df8f507e118b393007c3958358a830cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432976"
---
# <a name="iclrstrongname2-interface"></a>ICLRStrongName2 — Interfejs
Zapewnia możliwość tworzenia silnych nazw za pomocą grupy SHA-2 algorytmów wyznaczania wartości skrótu Secure (SHA-256, SHA-384 i SHA-512).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[StrongNameGetPublicKeyEx, metoda](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|Pobiera klucz publiczny z pary kluczy publiczny/prywatny i określa algorytm wyznaczania wartości skrótu i algorytm podpisu.|  
|[StrongNameSignatureVerificationEx2, metoda](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|Weryfikuje podpis zestawu o silnej nazwie i udostępnia mapowanie z ECMA klucza do rzeczywistego klucza.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
