---
title: "ICorConfiguration::AddDebuggerSpecialThread — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.AddDebuggerSpecialThread
api_location: mscoree.dll
api_type: COM
f1_keywords: AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2041a45cb80a08b2322f23e820f89b4bb71f845
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a>ICorConfiguration::AddDebuggerSpecialThread — Metoda
Do debugowania usług wskazuje, że określonego wątku powinien mieć możliwość kontynuowania wykonywania, gdy debuger został zatrzymany w scenariuszach debugowania zarządzanych lub niezarządzanych aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSpecialThreadId`  
 [in] Identyfikator wątku, który powinien mieć możliwość kontynuowania wykonywania.  
  
## <a name="remarks"></a>Uwagi  
 Określony wątek będzie nie można uruchamiać kodu zarządzanego lub wprowadź środowiska uruchomieniowego w dowolny sposób. Przykładem takich wątku może być wątek w trakcie obsługi debugery starszych skryptu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorConfiguration, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
