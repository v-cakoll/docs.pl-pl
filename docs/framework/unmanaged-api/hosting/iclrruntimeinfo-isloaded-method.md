---
title: ICLRRuntimeInfo::IsLoaded — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: 3275a69683a312340f35841815685066def10b23
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762529"
---
# <a name="iclrruntimeinfoisloaded-method"></a>ICLRRuntimeInfo::IsLoaded — Metoda
Wskazuje, czy środowisko uruchomieniowe języka wspólnego (CLR) skojarzone z interfejsem [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) jest załadowane do procesu. Środowisko uruchomieniowe może zostać załadowane bez również uruchamiania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a>Parametry  
 `hndProcess`  
 podczas Dojście do procesu.  
  
 `pbLoaded`  
 [out] `true` Jeśli środowisko CLR jest załadowane do procesu; w przeciwnym razie `false` .  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pbLoaded`ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest zgodna z poprzednimi wersjami przy użyciu następujących funkcji i interfejsów:  
  
- Interfejs [ICorRuntimeHost](icorruntimehost-interface.md) (w interfejsie API hostingu .NET Framework w wersji 1).  
  
- Interfejs [ICLRRuntimeHost](iclrruntimehost-interface.md) (w interfejsie API hostingu .NET Framework 2,0).  
  
- Przestarzałe `CorBindTo*` funkcje (zobacz [przestarzałe funkcje hostingu środowiska CLR](deprecated-clr-hosting-functions.md) w interfejsie API hostingu .NET Framework 2,0).  
  
 Host może wywołać jedną z przestarzałych `CorBindTo*` funkcji, takich jak funkcja [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) , aby utworzyć wystąpienie konkretnej wersji środowiska CLR. Następnie host może wywołać metodę [ICLRMetaHost:: GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) i określić ten sam numer wersji, aby uzyskać Interfejs [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .  
  
 Jeśli host następnie wywoła `IsLoaded` metodę w zwróconym interfejsie [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , `pbLoaded` zwraca `true` ; w przeciwnym razie zwraca `false` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRRuntimeInfo, interfejs](iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
- [Hosting](index.md)
