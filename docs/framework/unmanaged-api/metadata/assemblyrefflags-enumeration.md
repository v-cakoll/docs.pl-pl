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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc98b2421d23ffd6dfb716a8cc782b46a9d59ce0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128899"
---
# <a name="assemblyrefflags-enumeration"></a>AssemblyRefFlags — Wyliczenie
Zawiera wartości, które opisano funkcje odwołania do zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`arfFullOriginator`|Określa, że odwołanie do zestawu zawiera pełną, bez haszowania informacji o wydawcy zestawu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [IMetaDataAssemblyEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [DefineAssemblyRef, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
