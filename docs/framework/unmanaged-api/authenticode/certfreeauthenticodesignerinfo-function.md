---
title: Funkcja CertFreeAuthenticodeSignerInfo
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 357a2ca0ffc733adb14a21624cbe28fb754c8240
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776729"
---
# <a name="certfreeauthenticodesignerinfo-function"></a>Funkcja CertFreeAuthenticodeSignerInfo
Zwalnia zasoby przydzieloną dla struktury [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `pSignerInfo`  
 [in. out] Informacje o logowaniu do zwolnienia. Zobacz strukturę [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`Jeśli funkcja się powiedzie. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz także

- [Authenticode](index.md)
