---
title: Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae7879e1f6598108d839287792ed441391764ae2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776647"
---
# <a name="axl_authenticode_timestamper_info-structure"></a>Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO
Definiuje informacje o sygnaturze czasowym Authenticode.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`cbSize`|Rozmiar tej struktury.|  
|`dwError`|Kod błędu.|  
|`algHash`|Algorytm wyznaczania wartości skrótu.|  
|`ftTimestamp`|Godzina sygnatury czasowej.|  
|`pChainContext`|Kontekst łańcucha sygnatury czasowej.  Zobacz strukturę [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .|  
  
## <a name="see-also"></a>Zobacz także

- [Authenticode](index.md)
