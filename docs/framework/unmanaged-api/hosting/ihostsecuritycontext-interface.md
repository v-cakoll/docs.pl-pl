---
title: IHostSecurityContext — Interfejs
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: f6e25bfe11880730f6f447ccc0406d716d185624
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501498"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext — Interfejs
Umożliwia środowisko uruchomieniowe języka wspólnego (CLR), aby zachować informacje kontekstu zabezpieczeń zaimplementowane przez hosta.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Capture, metoda](ihostsecuritycontext-capture-method.md)|Pobiera klon `IHostSecurityContext` wystąpienia zwróconego z wywołania do [IHostSecurityManager:: GetSecurityContext —](ihostsecuritymanager-getsecuritycontext-method.md).|  
  
## <a name="remarks"></a>Uwagi  
 Host może kontrolować cały dostęp kodu do tokenów wątków przez środowisko CLR i kod użytkownika. Może także zapewnić, że pełne informacje kontekstu zabezpieczeń są przesyłane przez operacje asynchroniczne lub punkty kodowe z ograniczonym dostępem do kodu. `IHostSecurityContext`hermetyzuje informacje kontekstu zabezpieczeń, które są nieprzezroczyste dla środowiska uruchomieniowego. Środowisko uruchomieniowe przechwytuje te informacje przy użyciu `Capture` i przenosi je między elementami roboczymi puli wątków, wykonywaniem finalizatora oraz konstruktorami modułów i klas.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRHostProtectionManager, interfejs](iclrhostprotectionmanager-interface.md)
- [IHostSecurityManager, interfejs](ihostsecuritymanager-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
