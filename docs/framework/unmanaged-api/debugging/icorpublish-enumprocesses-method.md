---
title: ICorPublish::EnumProcesses — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 5f0dd814ad5adfa1b0dd7199530a3f993634a548
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121797"
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses — Metoda
Pobiera moduł wyliczający dla zarządzanych procesów uruchomionych na tym komputerze.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Type`  
 Wartość wyliczenia [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) , która określa typ procesu do pobrania. W bieżącej wersji tylko COR_PUB_MANAGEDONLY jest prawidłowy.  
  
 `ppIEnum`  
 Wskaźnik do adresu wystąpienia [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) , który jest modułem wyliczającym procesy.  
  
## <a name="remarks"></a>Uwagi  
 Kolekcja procesów modułu wyliczającego jest oparta na migawce procesów, które są uruchomione, gdy wywoływana jest metoda `EnumProcesses`. Moduł wyliczający nie będzie zawierać żadnych procesów kończących się przed lub po wywołaniu `EnumProcesses`.  
  
 Metoda `EnumProcesses` może być wywoływana więcej niż raz w tym wystąpieniu [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) , aby utworzyć nową, aktualną kolekcję procesów. Kolejne wywołania metody `EnumProcesses` nie będą miały wpływ na istniejące kolekcje.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorPublish, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
