---
title: CreateICeeFileGen — Funkcja
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 566f73335861a8eb769b21a254e0e93b51a78d02
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151817"
---
# <a name="createiceefilegen-function"></a>CreateICeeFileGen — Funkcja
Tworzy [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) obiektu.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ceeFileGen`  
 [out] Wskaźnik do adresów nowej `ICeeFileGen` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów COM.  
  
## <a name="remarks"></a>Uwagi  
 `ICeeFileGen` Obiekt jest używany do tworzenia języka wspólnego plików przenośnych plików wykonywalnych (PE) środowiska uruchomieniowego (języka wspólnego CLR).  
  
 Wywołaj [destroyiceefilegen —](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) funkcję, aby zniszczyć `ICeeFileGen` obiektu po zakończeniu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ICeeFileGen.h  
  
 **Biblioteka:** MSCorPE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
