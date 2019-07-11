---
title: CorImportOptions — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38c0937804eb82d1c96a605b55a00784ba58fe13
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781824"
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions — Wyliczenie
Zawiera wartości flagi, które kontrolują zachowanie podczas Importowanie zestawu poza bieżącym zakresem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MDImportOptionDefault`|Wskazuje zachowanie domyślne, czyli aby pominąć usuniętych rekordów.|  
|`MDImportOptionAll`|Wskazuje, że można wyliczyć wszystkie metadane.|  
|`MDImportOptionAllTypeDefs`|Wskazuje, że można wyliczyć wszystkie definicje typów, w tym usuniętych.|  
|`MDImportOptionAllMethodDefs`|Wskazuje, że można wyliczyć wszystkie MethodDefs, w tym usuniętych.|  
|`MDImportOptionAllFieldDefs`|Wskazuje, że można wyliczyć wszystkie FieldDefs, w tym usuniętych.|  
|`MDImportOptionAllProperties`|Wskazuje, że można wyliczyć wszystkie PropertyDefs, w tym usuniętych.|  
|`MDImportOptionAllEvents`|Wskazuje, że można wyliczyć wszystkie EventDefs, w tym usuniętych.|  
|`MDImportOptionAllCustomAttributes`|Wskazuje, że można wyliczyć wszystkich atrybutów niestandardowych, w tym usuniętych.|  
|`MDImportOptionAllExportedTypes`|Wskazuje, że można wyliczyć wszystkich typów eksportowanych, w tym usuniętych z nich.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
