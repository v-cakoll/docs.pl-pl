---
title: ICLRMetaHost::RequestRuntimeLoadedNotification — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61fce3e06b5245872f7061716e8d995dd5f5043c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984649"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification — Metoda
Oferuje funkcję wywołania zwrotnego, która może być wywoływana, gdy typowe wersję środowiska uruchomieniowego (języka wspólnego CLR) języka jest ładowana jako pierwsza, ale jeszcze nie rozpoczęty. Ta metoda zastępuje [lockclrversion —](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCallbackFunction`  
 [in] Funkcja wywołania zwrotnego, która jest wywoływana po załadowaniu nowego środowiska uruchomieniowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pCallbackFunction` ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie zwrotne działa w następujący sposób:  
  
- Wywołanie zwrotne jest wywoływane tylko wtedy, gdy środowisko uruchomieniowe jest ładowany po raz pierwszy.  
  
- Wywołanie zwrotne nie jest wywoływany w przypadku obciążeń współużytkowane tego samego środowiska uruchomieniowego.  
  
- W przypadku obciążeń nie obsługującą środowiska uruchomieniowego są serializowane wywołania do funkcji wywołania zwrotnego.  
  
 Funkcja wywołania zwrotnego zawiera poniższy prototyp:  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 Prototypy funkcji wywołania zwrotnego są następujące:  
  
- `pfnCallbackThreadSet`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- `pfnCallbackThreadUnset`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 Jeśli host zamierza obciążenia lub powodują, że innego środowiska uruchomieniowego do załadowania w sposób współużytkowane `pfnCallbackThreadSet` i `pfnCallbackThreadUnset` parametry, które znajdują się w wywołania zwrotnego funkcji muszą być używane w następujący sposób:  
  
- `pfnCallbackThreadSet` musi zostać wywołany przez wątek, który może spowodować obciążenia środowiska uruchomieniowego, przed próbą takie obciążenia.  
  
- `pfnCallbackThreadUnset` musi być wywoływana, gdy wątek już nie spowoduje obciążenia środowiska uruchomieniowego (i przed powrotem po początkowej wywołania zwrotnego).  
  
- `pfnCallbackThreadSet` i `pfnCallbackThreadUnset` są nie obsługującą.  
  
> [!NOTE]
>  Hostowanie aplikacji nie mogą wywoływać `pfnCallbackThreadSet` i `pfnCallbackThreadUnset` poza zakresem `pCallbackFunction` parametru.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRMetaHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
