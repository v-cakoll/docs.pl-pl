---
title: Funkcja CertFreeAuthenticodeSignerInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertFreeAuthenticodeSignerInfo
api_location: clr.dll
api_type: DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f922cdba8bcfce6c9ff4543f6aea5bacfdc60ab0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="certfreeauthenticodesignerinfo-function"></a>Funkcja CertFreeAuthenticodeSignerInfo
Zwalnia zasoby przydzielone dla [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSignerInfo`  
 [w, out] Informacje o osobie podpisującej do zwolnienia. Zobacz [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) struktury.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`Jeśli funkcja zakończy się powodzeniem. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
