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
ms.openlocfilehash: 1cb84b94b37a2e9e8dd4d20d09cbca82db290c0f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009458"
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags — Wyliczenie
Zawiera wartości opisujące funkcje czasu wykonywania zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`afImplicitExportedTypes`|Określa, że eksportowane definicje typów są niejawne w obrębie plików wchodzących w skład zestawu. W .NET Framework wersje 1,0 i 1,1 Ta wartość jest zawsze ustawiana jako ustawiona.|  
|`afImplicitResources`|Określa, że definicje zasobów są niejawne w obrębie plików wchodzących w skład zestawu. W .NET Framework 1,0 i 1,1 Ta wartość jest zawsze przyjmowana jako ustawiona.|  
|`afNonSideBySideAppDomain`|Określa, że zestaw nie może być wykonywany z innymi wersjami, jeśli są uruchomione w tej samej domenie aplikacji.|  
|`afNonSideBySideProcess`|Określa, że zestaw nie może być wykonywany z innymi wersjami, jeśli są uruchomione w tym samym procesie.|  
|`afNonSideBySideMachine`|Określa, że zestaw nie może być wykonywany z innymi wersjami, jeśli są uruchomione na tym samym komputerze.|  
  
## <a name="remarks"></a>Uwagi  
 Wartości między 0x0010 i 0x0070, włącznie, służą do opisywania funkcji zgodności Side-by-Side w przywoływanym zestawie. Jeśli żadna z tych wartości nie zostanie ustawiona, przyjmuje się, że zestaw jest zgodny ze sobą.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MsCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
- [IMetaDataAssemblyEmit — Interfejs](imetadataassemblyemit-interface.md)
