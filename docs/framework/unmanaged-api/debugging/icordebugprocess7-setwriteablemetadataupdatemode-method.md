---
title: Metoda ICorDebugProcess7::SetWriteableMetadataUpdateMode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e901fd623893b9c03e1b5835adc72c6bd225ead4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) wartości wyliczenia, która określa, czy w pamięci aktualizacji metadanych w procesie docelowym są widoczne (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) lub nie jest widoczny (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) do debugera.  
  
## <a name="remarks"></a>Uwagi  
 Aktualizacji metadanych proces docelowy mogą pochodzić z Edytuj i Kontynuuj, profilera, lub <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugProcess7, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
