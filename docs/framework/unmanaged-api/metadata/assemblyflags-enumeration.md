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
ms.openlocfilehash: 7c86a4fd2788c8ea2df5d9e54c5c221afd179704
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091424"
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags — Wyliczenie
Zawiera wartości, które opisują zestawu funkcji środowiska uruchomieniowego.  
  
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
|`afImplicitExportedTypes`|Określa, czy niejawne w ramach plików, wchodzące w skład zestawu definicji eksportowanego typu. W .NET Framework w wersji 1.0 i 1.1 Ta wartość jest zawsze zakłada się, że można ustawić.|  
|`afImplicitResources`|Określa, że definicje są niejawne w ramach plików, wchodzące w skład zestawu. W .NET Framework 1.0 i 1.1 Ta wartość jest zawsze zakłada się, że można ustawić.|  
|`afNonSideBySideAppDomain`|Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są uruchomione w tej samej domenie aplikacji.|  
|`afNonSideBySideProcess`|Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są uruchomione w tym samym procesie.|  
|`afNonSideBySideMachine`|Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są uruchomione na tym samym komputerze.|  
  
## <a name="remarks"></a>Uwagi  
 Wartości między 0x0010 i 0x0070 włącznie, są używane do opisywania funkcje zgodności side-by-side przywoływanego zestawu. Jeśli żadna z tych wartości są ustawione, zestaw zakłada się, że zgodne side-by-side.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MsCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
