---
title: "ICLRMetaHost::RequestRuntimeLoadedNotification — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 32eb92263685bc3be9f0c28dea88ecfa78c2b52c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification — Metoda
Udostępnia funkcję wywołania zwrotnego, które na pewno jest wywoływana, gdy wspólne środowisko uruchomieniowe (języka wspólnego CLR) w wersji językowej jest ładowana jako pierwsza, ale jeszcze nie uruchomiono. Ta metoda zastępuje [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCallbackFunction`  
 [in] Funkcja wywołania zwrotnego, które jest wywoływane, gdy nowe środowisko uruchomieniowe został załadowany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pCallbackFunction`ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołania zwrotnego działa w następujący sposób:  
  
-   Wywołanie zwrotne jest wywoływane tylko wtedy, gdy środowisko wykonawcze jest załadowany po raz pierwszy.  
  
-   Wywołanie zwrotne nie jest wywoływany w przypadku współużytkowane obciążeń tego samego środowiska uruchomieniowego.  
  
-   W przypadku obciążeń runtime nie obsługującą wywołań funkcji wywołania zwrotnego są serializowane.  
  
 Funkcja wywołania zwrotnego zawiera następujące prototypu:  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 Prototypy funkcji wywołania zwrotnego są następujące:  
  
-   `pfnCallbackThreadSet`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   `pfnCallbackThreadUnset`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 Jeśli host zamierza obciążenia lub spowodować innego środowiska uruchomieniowego do załadowania w sposób współużytkowane `pfnCallbackThreadSet` i `pfnCallbackThreadUnset` parametrów, które są podane podczas wywołania zwrotnego funkcja musi być używany w następujący sposób:  
  
-   `pfnCallbackThreadSet`musi zostać wywołany w wątku, który może spowodować, że obciążenia środowiska wykonawczego przed próbą takie obciążenia.  
  
-   `pfnCallbackThreadUnset`musi być wywoływana, gdy wątek już spowoduje obciążenia środowiska uruchomieniowego (i przed powrotem z wywołania zwrotnego początkowej).  
  
-   `pfnCallbackThreadSet`i `pfnCallbackThreadUnset` są nie obsługującą.  
  
> [!NOTE]
>  Host aplikacji nie mogą wywoływać `pfnCallbackThreadSet` i `pfnCallbackThreadUnset` poza zakresem `pCallbackFunction` parametru.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRMetaHost — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
