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
ms.openlocfilehash: 3be8a004be752af8a8675a3499bdb6cbfd785840
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009200"
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
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
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
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
