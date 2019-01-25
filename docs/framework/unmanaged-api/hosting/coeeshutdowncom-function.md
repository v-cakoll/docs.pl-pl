---
title: CoEEShutDownCOM — Funkcja
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 755ff827300dd9fef5944924f6373415f6d8fa6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568585"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM — Funkcja
Wymusza środowisko uruchomieniowe języka wspólnego (CLR), aby zwolnić wszystkie wskaźniki interfejsu, którą przechowuje wewnątrz wywoływanych otok środowiska uruchomieniowego (RCW). To powoduje zwolnienie wszystkich RCW pamięci podręcznych. Ta funkcja globalna jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Zamiast tego należy użyć punktu wejścia dla określonego środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Uwagi  
 `CoEEShutDownCOM` Funkcji najpierw zwalnia RCW we wszystkich kontekstach i wszystkich pamięci podręcznych, a następnie usuwa wszelkie powiadomienia zakończenia istniejące w Instalatorze. Nie zwalnianie biblioteki DLL występuje.  
  
> [!CAUTION]
>  Ta funkcja ma wpływ na wszystkie środowiska uruchomieniowe, które są ładowane do procesu.  
  
 Począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], wywołać punkt wejścia dla tej funkcji, od określonego środowiska uruchomieniowego, chcesz mieć wpływ. Aby uzyskać punkt wejścia, należy wywołać [iclrruntimeinfo::GetProcAddress —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metodę i określić "coeeshutdowncom —".  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
