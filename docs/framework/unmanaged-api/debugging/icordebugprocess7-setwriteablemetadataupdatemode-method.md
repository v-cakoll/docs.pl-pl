---
title: Metoda ICorDebugProcess7::SetWriteableMetadataUpdateMode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94e2f1c13c91c50daa5730898adf0aedf00f6579
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092620"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a>Metoda ICorDebugProcess7::SetWriteableMetadataUpdateMode
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Określa, jak debuger obsługuje aktualizacje w pamięci do metadanych w ramach procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) wartości wyliczenia, która określa, czy aktualizacje metadanych w procesie docelowym w pamięci są widoczne (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) lub nie jest widoczny (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) do debugera.  
  
## <a name="remarks"></a>Uwagi  
 Aktualizacji metadanych procesu docelowego mogą pochodzić z Edit and Continue, program profilujący, lub <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejs ICorDebugProcess7](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
