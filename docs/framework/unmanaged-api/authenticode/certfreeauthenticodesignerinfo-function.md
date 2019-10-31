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
ms.openlocfilehash: a233e0b8d17b9ee61b1991086f794c9fb20f89e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099835"
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
 `S_OK`, jeśli funkcja się powiedzie. W przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz także

- [Authenticode](index.md)
