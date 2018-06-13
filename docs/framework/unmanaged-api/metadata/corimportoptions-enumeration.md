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
ms.openlocfilehash: 7078b2eb98c15b7229132076da8af4691032bb08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441795"
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions — Wyliczenie
Zawiera wartości flagi, które kontrolują zachowanie podczas Import zestawu spoza zakresu.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`MDImportOptionDefault`|Wskazuje zachowanie domyślne, które mają pominąć usuniętych rekordów.|  
|`MDImportOptionAll`|Wskazuje, że można wyliczyć wszystkich metadanych.|  
|`MDImportOptionAllTypeDefs`|Wskazuje, czy wszystkie definicje typów, w tym usunięto te należy wyliczyć.|  
|`MDImportOptionAllMethodDefs`|Wskazuje, że można wyliczyć wszystkich MethodDefs, w tym tych usuniętych.|  
|`MDImportOptionAllFieldDefs`|Wskazuje, że można wyliczyć wszystkich FieldDefs, w tym tych usuniętych.|  
|`MDImportOptionAllProperties`|Wskazuje, że można wyliczyć wszystkich PropertyDefs, w tym tych usuniętych.|  
|`MDImportOptionAllEvents`|Wskazuje, że można wyliczyć wszystkich EventDefs, w tym tych usuniętych.|  
|`MDImportOptionAllCustomAttributes`|Wskazuje, że można wyliczyć wszystkich atrybutów niestandardowych, w tym usunięto te.|  
|`MDImportOptionAllExportedTypes`|Wskazuje, czy można wyliczyć wszystkich typów wyeksportowany, w tym tych usuniętych.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
