---
title: InitDbgTransportManager — Funkcja
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
ms.openlocfilehash: 2d67bee3ea0e57080179b3fbb7e0b4193860c44d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103288"
---
# <a name="initdbgtransportmanager-function"></a>InitDbgTransportManager — Funkcja
Inicjuje menedżera transportu, aby połączyć się ze zdalnym elementem docelowym na potrzeby wyliczenia procesu i środowiska uruchomieniowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Prawnego.  
  
 E_OUTOFMEMORY  
 Funkcja nie może przydzielić pamięci dla menedżera transportu.  
  
 E_FAIL (lub inne kody powrotne E_)  
 Inne błędy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Biblioteka:** mscordbi_macx86. dll  
  
 **.NET Framework wersje:** 3,5 SP1
