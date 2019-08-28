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
ms.openlocfilehash: 164384f043a1722ace6e5c4098cb31c4327cba1e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044060"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM — Funkcja
Wymusza, aby środowisko uruchomieniowe języka wspólnego (CLR) zwolnił wszystkie wskaźniki interfejsu, które znajdują się wewnątrz wywoływanych otok (RCW) środowiska uruchomieniowego. Ma to wpływ na zwalnianie wszystkich pamięci podręcznych OTOKi. Ta funkcja globalna jest przestarzała w .NET Framework 4. Zamiast tego należy użyć punktu wejścia dla określonego środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Uwagi  
 `CoEEShutDownCOM` Funkcja najpierw zwalnia wszystkie RCW we wszystkich kontekstach i we wszystkich pamięciach podręcznych, a następnie usuwa wszelkie powiadomienia o rozrywaniu istniejące w instalatorze. Brak wyładowywania biblioteki DLL.  
  
> [!CAUTION]
> Ta funkcja ma wpływ na wszystkie środowiska uruchomieniowe, które są ładowane do procesu.  
  
 Począwszy od .NET Framework 4, wywołaj punkt wejścia dla tej funkcji w konkretnym środowisku uruchomieniowym, którego chcesz dotyczyć. Aby uzyskać punkt wejścia, wywołaj metodę [ICLRRuntimeInfo:: GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) i określ wartość "CoEEShutDownCOM —".  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** Cor. h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
