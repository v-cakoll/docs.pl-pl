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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2779138a0999e34ad6424d76ddfebbcfdf611d58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422900"
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses — Metoda
Pobiera moduł wyliczający dla zarządzanych procesów uruchomionych na tym komputerze.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Type`  
 Wartość [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) wyliczenie określający typ procesu, które mają zostać pobrane. W bieżącej wersji tylko COR_PUB_MANAGEDONLY jest prawidłowy.  
  
 `ppIEnum`  
 Wskaźnik do adresu [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) wystąpienie, które jest modułem wyliczającym procesów.  
  
## <a name="remarks"></a>Uwagi  
 Moduł wyliczający kolekcja procesów jest oparta na migawki procesów, które są uruchomione podczas obliczania `EnumProcesses` metoda jest wywoływana. Moduł wyliczający nie będzie zawierać wszystkie procesy, które kończy się przed lub uruchomić po `EnumProcesses` jest wywoływana.  
  
 `EnumProcesses` — Metoda może być wywołany więcej niż raz w tym [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) wystąpienia, aby utworzyć nową kolekcję aktualne procesów. Nie wpłynie istniejących zbiorach przez kolejne wywołania `EnumProcesses` metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorPublish, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
