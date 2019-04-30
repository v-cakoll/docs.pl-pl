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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763727"
---
# <a name="iclrstrongname2-interface"></a>ICLRStrongName2 — Interfejs
Zapewnia możliwość tworzenia silnych nazw za pomocą grupy SHA-2 algorytmów wyznaczania wartości skrótu Secure (SHA-256, SHA-384 i SHA-512).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[StrongNameGetPublicKeyEx, metoda](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|Pobiera klucz publiczny z pary kluczy publiczny/prywatny, a następnie określa algorytm wyznaczania wartości skrótu i algorytm podpisu.|  
|[StrongNameSignatureVerificationEx2, metoda](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|Weryfikuje podpis zestaw o silnej nazwie, a następnie udostępnia mapowanie klucz ECMA do rzeczywistego klucza.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
