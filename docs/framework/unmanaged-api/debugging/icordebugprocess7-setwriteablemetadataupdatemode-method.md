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
ms.openlocfilehash: 6de75e1e27660ac91bd6320a501db47f3b055fb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212259"
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
 Wartość wyliczenia [WriteableMetadataUpdateMode](writeablemetadataupdatemode-enumeration.md) określająca, czy aktualizacje w pamięci dla metadanych w procesie docelowym są widoczne ( `WriteableMetadataUpdateMode::AlwaysShowUpdates` ) lub niewidoczne () w `WriteableMetadataUpdateMode::LegacyCompatPolicy` debugerze.  
  
## <a name="remarks"></a>Uwagi  
 Aktualizacje metadanych procesu docelowego mogą pochodzić z narzędzia Edytuj i Kontynuuj, profilera lub <xref:System.Reflection.Emit?displayProperty=nameWithType> .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Interfejs ICorDebugProcess7](icordebugprocess7-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
