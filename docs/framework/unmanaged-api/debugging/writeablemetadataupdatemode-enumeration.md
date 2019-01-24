---
title: Wyliczenie WriteableMetadataUpdateMode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b49b63049d33c41757db1abae82ed2a4e266b42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572217"
---
# <a name="writeablemetadataupdatemode-enumeration"></a>Wyliczenie WriteableMetadataUpdateMode
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Zawiera wartości, które określają, czy aktualizacje metadanych w pamięci są widoczne dla debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Nazwa elementu członkowskiego|Opis|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|Podczas wprowadzania aktualizacji w pamięci do metadanych widoczne, należy zachować zgodność z poprzednimi wersjami programu .NET Framework. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.|  
|`AlwaysShowUpdates`|Wyświetlaj aktualizacje w pamięci do metadanych do debugera.|  
  
## <a name="remarks"></a>Uwagi  
 Członek `WriteableMetadataUpdateMode` wyliczenia mogą być przekazywane do [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) metodę, aby kontrolować, czy w pamięci aktualizacje metadanych w procesie docelowym są widoczne dla debugera.  
  
 `LegacyCompatPolicy` Opcji wymusza takie samo zachowanie, jak w wersjach programu .NET Framework przed 4.5.2. Często oznacza to, metadane aktualizacji nie jest widoczny. Wywołania metod debugowania przekształcić niejawnie debugera, aby aktualizacje były widoczne. Na przykład, jeśli jest debugera przekazuje [ICorDebugILFrame::GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) indeksu w zmiennej, nie znaleziono metody oryginalnych metadanych wszystkie metadane dla modułu jest aktualizowana w celu dopasowania bieżący stan migawki proces. Innymi słowy, za pomocą `LegacyCompatPolicy` debuger może być wyświetlona żadnego, niektórych lub wszystkich aktualizacje dostępne metadane, w zależności od tego, w jaki sposób używa innych części niezarządzanego interfejsu API debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [SetWriteableMetadataUpdateMode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
