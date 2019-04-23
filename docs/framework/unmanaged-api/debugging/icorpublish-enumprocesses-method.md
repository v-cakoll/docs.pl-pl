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
ms.openlocfilehash: eb4096b0ae083e0b6c0598ea18cc8b33c2fdfe3e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116298"
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses — Metoda
Pobiera moduł wyliczający dla zarządzanego procesów uruchomionych na tym komputerze.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Type`  
 Wartość [cor_pub_enumprocess —](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) wyliczenie, który określa typ procesu, które mają zostać pobrane. W bieżącej wersji COR_PUB_MANAGEDONLY tylko jest prawidłowa.  
  
 `ppIEnum`  
 Wskaźnik na adres [icorpublishprocessenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) wystąpienia, które jest moduł wyliczający procesów.  
  
## <a name="remarks"></a>Uwagi  
 Moduł wyliczający kolekcja procesów opiera się na migawki procesów, które są uruchomione podczas `EnumProcesses` metoda jest wywoływana. Moduł wyliczający nie będzie zawierać wszystkie procesy, które kończy się przed lub uruchom po `EnumProcesses` jest wywoływana.  
  
 `EnumProcesses` Metoda może być wywoływana więcej niż raz w tym [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) wystąpienia, aby utworzyć nową kolekcję aktualne procesów. Nie będzie mieć wpływ na istniejących kolekcji przez kolejne wywołania z `EnumProcesses` metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorPublish, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
