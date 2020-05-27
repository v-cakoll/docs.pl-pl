---
title: AssemblyRefFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- AssemblyRefFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyRefFlags
helpviewer_keywords:
- AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type:
- apiref
ms.openlocfilehash: 1307f555c9d8b6d28febcf25db89ae856c143d71
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009408"
---
# <a name="assemblyrefflags-enumeration"></a>AssemblyRefFlags — Wyliczenie
Zawiera wartości opisujące funkcje odwołania do zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`arfFullOriginator`|Określa, że odwołanie do zestawu zawiera pełne, niezmieszane informacje o wydawcy zestawu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
- [IMetaDataAssemblyEmit — Interfejs](imetadataassemblyemit-interface.md)
- [DefineAssemblyRef — Metoda](imetadataassemblyemit-defineassemblyref-method.md)
