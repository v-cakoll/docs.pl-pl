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
ms.openlocfilehash: 0d2b82bc056acd2e620461081b5f8c9d45fc152c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490647"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM — Funkcja
Wymusza środowisko uruchomieniowe języka wspólnego (CLR), aby zwolnić wszystkie wskaźniki interfejsu, którą przechowuje wewnątrz wywoływanych otok środowiska uruchomieniowego (RCW). To powoduje zwolnienie wszystkich RCW pamięci podręcznych. Ta funkcja globalna jest przestarzała w programie .NET Framework 4. Zamiast tego należy użyć punktu wejścia dla określonego środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
