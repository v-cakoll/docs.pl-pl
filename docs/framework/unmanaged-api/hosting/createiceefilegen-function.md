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
ms.openlocfilehash: 57163ccfcc6dff343a8bbc7d63564ae6b57b5ff6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490502"
---
# <a name="createiceefilegen-function"></a>CreateICeeFileGen — Funkcja
Tworzy [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) obiektu.  
  
 Ta funkcja jest przestarzała w programie .NET Framework 4.  
  
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
