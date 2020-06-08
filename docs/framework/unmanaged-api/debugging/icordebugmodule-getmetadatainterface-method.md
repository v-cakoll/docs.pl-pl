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
ms.openlocfilehash: f5d0dd7a99087b21a5f827e4dce0f6342ae7b25a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501771"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a>ICorDebugModule::GetMetaDataInterface — Metoda
Pobiera obiekt interfejsu metadanych, którego można użyć do sprawdzenia metadanych dla modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 podczas Identyfikator odwołania, który określa interfejs metadanych.  
  
 `ppObj`  
 określoną Wskaźnik do adresu `T:IUnknown` obiektu, który jest jednym z [interfejsów metadanych](../metadata/metadata-interfaces.md).  
  
## <a name="remarks"></a>Uwagi  
 Debuger może użyć `GetMetaDataInterface` metody, aby utworzyć kopię oryginalnych metadanych dla modułu, który musi wykonać w celu edytowania tego modułu. Debuger wywołuje `GetMetaDataInterface` , aby uzyskać obiekt interfejsu [IMetaDataEmit](../metadata/imetadataemit-interface.md) dla modułu, a następnie wywołuje [IMetaDataEmit:: SaveToMemory —](../metadata/imetadataemit-savetomemory-method.md) , aby zapisać kopię metadanych modułu w pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Metadane](../metadata/index.md)
