---
title: ICorDebugModule::GetMetaDataInterface — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 398c48bfd30020efdb57861991c9541d412d3e0d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763435"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a>ICorDebugModule::GetMetaDataInterface — Metoda
Pobiera obiekt interfejsu metadanych, który może służyć do badać metadane dla modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 [in] Identyfikator odwołania, który określa interfejs metadanych.  
  
 `ppObj`  
 [out] Wskaźnik na adres `T:IUnknown` obiekt, który jest jednym z [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).  
  
## <a name="remarks"></a>Uwagi  
 Można użyć debugera `GetMetaDataInterface` metodę, aby utworzyć kopię odpowiednich oryginalnych metadanych dla modułu, który należy wykonać w celu edytowania tego modułu. Wywołuje debugera `GetMetaDataInterface` można pobrać [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) obiektu interfejsu modułu, następnie wywołuje [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) można zapisać kopię modułu metadanych w pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Metadane](../../../../docs/framework/unmanaged-api/metadata/index.md)
