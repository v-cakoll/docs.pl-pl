---
title: "ICorRuntimeHost::UnloadDomain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.UnloadDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 067b60b9da02300e9e7316712d0058a61ab8a697
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostunloaddomain-method"></a>ICorRuntimeHost::UnloadDomain — Metoda
Zwalnia domeny określonej aplikacji w bieżącym procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [in] Wskaźnik typu <xref:System._AppDomain?displayProperty=nameWithType> reprezentujący domeny, która ma zostać zwolniony.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Operacja powiodła się.|  
|WARTOŚCI S_FALSE|Nie można ukończyć operacji.|  
|E_FAIL|Wystąpił nieznany, poważnej awarii. Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie. Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersja platformy .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
