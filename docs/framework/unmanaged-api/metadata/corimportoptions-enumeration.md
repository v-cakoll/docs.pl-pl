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
ms.openlocfilehash: 44d1776e2902988353ef4fd58aca20e56203b9da
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442845"
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions — Wyliczenie
Zawiera wartości flag kontrolujące zachowanie podczas importu zestawu poza bieżącym zakresem.  
  
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
  
## <a name="members"></a>Members  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MDImportOptionDefault`|Wskazuje zachowanie domyślne, co oznacza pominięcie usuniętych rekordów.|  
|`MDImportOptionAll`|Wskazuje, że wszystkie metadane powinny być wyliczane.|  
|`MDImportOptionAllTypeDefs`|Wskazuje, że wszystkie definicje typów, włącznie z usuniętymi, powinny być wyliczane.|  
|`MDImportOptionAllMethodDefs`|Wskazuje, że wszystkie MethodDefs, włącznie z usuniętymi, powinny być wyliczane.|  
|`MDImportOptionAllFieldDefs`|Wskazuje, że wszystkie FieldDefs, włącznie z usuniętymi, powinny być wyliczane.|  
|`MDImportOptionAllProperties`|Wskazuje, że wszystkie PropertyDefs, włącznie z usuniętymi, powinny być wyliczane.|  
|`MDImportOptionAllEvents`|Wskazuje, że wszystkie EventDefs, włącznie z usuniętymi, powinny być wyliczane.|  
|`MDImportOptionAllCustomAttributes`|Wskazuje, że wszystkie atrybuty niestandardowe, w tym usunięte, powinny być wyliczane.|  
|`MDImportOptionAllExportedTypes`|Wskazuje, że wszystkie wyeksportowane typy, łącznie z usuniętymi, powinny być wyliczane.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
