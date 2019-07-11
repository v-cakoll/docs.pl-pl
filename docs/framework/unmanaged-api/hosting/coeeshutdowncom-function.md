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
- mscorsvr.dll
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
ms.openlocfilehash: 74548df512f68761b006e064a6db968e82b03813
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779122"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM — Funkcja
Wymusza środowisko uruchomieniowe języka wspólnego (CLR), aby zwolnić wszystkie wskaźniki interfejsu, którą przechowuje wewnątrz wywoływanych otok środowiska uruchomieniowego (RCW). To powoduje zwolnienie wszystkich RCW pamięci podręcznych. Ta funkcja globalna jest przestarzała w programie .NET Framework 4. Zamiast tego należy użyć punktu wejścia dla określonego środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Uwagi  
 `CoEEShutDownCOM` Funkcji najpierw zwalnia RCW we wszystkich kontekstach i wszystkich pamięci podręcznych, a następnie usuwa wszelkie powiadomienia zakończenia istniejące w Instalatorze. Nie zwalnianie biblioteki DLL występuje.  
  
> [!CAUTION]
>  Ta funkcja ma wpływ na wszystkie środowiska uruchomieniowe, które są ładowane do procesu.  
  
 Począwszy od programu .NET Framework 4, należy wywołać punkt wejścia dla tej funkcji, od określonego środowiska uruchomieniowego, które mają wpływ na. Aby uzyskać punkt wejścia, należy wywołać [iclrruntimeinfo::GetProcAddress —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metodę i określić "coeeshutdowncom —".  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
