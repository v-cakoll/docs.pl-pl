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
ms.openlocfilehash: 453486c9e3d98ffd6f0dcfa08e7a0a9a1c1d3342
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123389"
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a>Metoda ICorDebugProcess7::SetWriteableMetadataUpdateMode
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Konfiguruje sposób, w jaki Debuger obsługuje aktualizacje w pamięci do metadanych w procesie docelowym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 Wartość wyliczenia [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) określająca, czy aktualizacje w pamięci dla metadanych w procesie docelowym są widoczne (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) lub niewidoczne (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) do debugera.  
  
## <a name="remarks"></a>Uwagi  
 Aktualizacje metadanych procesu docelowego mogą pochodzić z narzędzia Edytuj i Kontynuuj, profilera lub <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess7, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
