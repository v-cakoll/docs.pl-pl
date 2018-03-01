---
title: "CoEEShutDownCOM — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ae339310c2bfd186cae798ff603d69735abeefd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM — Funkcja
Wymusza środowisko uruchomieniowe języka wspólnego (CLR), aby zwolnić wszystkie wskaźniki interfejsu, którą przechowuje wewnątrz wywoływane otoki środowiska uruchomieniowego (otoki RCW). To ustawienie zwalnia wszystkie otoki RCW pamięci podręcznych. Ta funkcja globalna jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. W zamian użyj punkt wejścia dla określonego środowiska wykonawczego.  
  
## <a name="syntax"></a>Składnia  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Uwagi  
 `CoEEShutDownCOM` Funkcji najpierw zwalnia wszystkie RCWs we wszystkich kontekstach i wszystkich usług pamięć podręczna i spowoduje usunięcie wszystkich istniejących w Instalatorze powiadomień zakończenia. Występuje, nie zwalnianie biblioteki DLL.  
  
> [!CAUTION]
>  Ta funkcja ma wpływ na wszystkie środowiska uruchomieniowe, które są ładowane do procesu.  
  
 Począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], wywołaj punkt wejścia dla tej funkcji na określonych ma wpływ na środowisko uruchomieniowe. Aby uzyskać punktu wejścia, należy wywołać [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metodę i określić "CoEEShutDownCOM".  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
