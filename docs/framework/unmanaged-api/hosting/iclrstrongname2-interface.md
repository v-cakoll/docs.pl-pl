---
title: "ICLRStrongName2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName2
helpviewer_keywords: ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9e9a88f1064c888d60e363be569d06458299143d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongname2-interface"></a>ICLRStrongName2 — Interfejs
Zapewnia możliwość tworzenia silnych nazw za pomocą grupy SHA-2 algorytmów wyznaczania wartości skrótu Secure (SHA-256, SHA-384 i SHA-512).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[StrongNameGetPublicKeyEx — metoda](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|Pobiera klucz publiczny z pary kluczy publiczny/prywatny i określa algorytm wyznaczania wartości skrótu i algorytm podpisu.|  
|[StrongNameSignatureVerificationEx2 — metoda](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|Weryfikuje podpis zestawu o silnej nazwie i udostępnia mapowanie z ECMA klucza do rzeczywistego klucza.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
