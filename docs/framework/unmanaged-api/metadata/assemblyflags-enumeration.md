---
title: AssemblyFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fc6d08e960b0ba82c76945a318ec723546f71b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444909"
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags — Wyliczenie
Zawiera wartości, które opisano funkcje wykonawcze języka zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`afImplicitExportedTypes`|Określa, że definicje wyeksportowanego typu niejawnych plików wchodzących w skład zestawu. W wersje programu .NET Framework 1.0 i 1.1 Ta wartość jest zawsze przyjęto, należy ustawić wartość.|  
|`afImplicitResources`|Określa, że niejawnych plików wchodzących w skład zestawu definicji zasobu. W .NET Framework 1.0 i 1.1 Ta wartość jest zawsze przyjęto, należy ustawić wartość.|  
|`afNonSideBySideAppDomain`|Określa, że zestaw nie można wykonać z innymi wersjami, jeśli działają w tej samej domenie aplikacji.|  
|`afNonSideBySideProcess`|Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są na nich uruchomione w tym samym procesie.|  
|`afNonSideBySideMachine`|Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są na nich uruchomione na tym samym komputerze.|  
  
## <a name="remarks"></a>Uwagi  
 Wartości między 0x0010 i 0x0070 włącznie, służą do opisywania funkcje zgodności side-by-side przywoływanego zestawu. Jeśli żadna z tych wartości, zestaw zakłada się, że side-by-side zgodny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MsCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
