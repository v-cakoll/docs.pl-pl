---
title: CorAssemblyFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eca4b66a3f7c1a96bb06827dde477f34cb904ba3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072717"
---
# <a name="corassemblyflags-enumeration"></a>CorAssemblyFlags — Wyliczenie
Zawiera wartości, które opisują metadane stosowane do kompilacji zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`afPublicKey`|Wskazuje, że odwołanie do zestawu zawiera pełną, bez haszowania klucz publiczny.|  
|`afPA_None`|Wskazuje, że architektura procesora jest nieokreślony.|  
|`afPA_MSIL`|Wskazuje, że architektura procesora jest neutralny (PE32).|  
|`afPA_x86`|Wskazuje, że architektura procesora jest x86 (PE32).|  
|`afPA_IA64`|Wskazuje, że architektura procesora jest Itanium (PE32 +).|  
|`afPA_AMD64`|Wskazuje, że architektura procesora jest AMD X64 (PE32 +).|  
|`afPA_ARM`|Wskazuje, że architektura procesora jest ARM (PE32).|  
|`afPA_NoPlatform`|Wskazuje, że zestaw jest zestaw odwołania; oznacza, że ma zastosowanie do dowolnej architekturze ale nie można uruchomić na dowolnej architektury. W związku z tym, Flaga jest taka sama jak `afPA_Mask`.|  
|`afPA_Specified`|Wskazuje, że flagi architektury procesora należy propagowane do `AssemblyRef` rekordu.|  
|`afPA_Mask`|Maska, która zawiera opis architektury procesora.|  
|`afPA_FullMask`|Określa, czy znajduje się opis architektury procesora.|  
|`afPA_Shift`|Wskazuje liczbę shift in flagi architektury procesora, do i z indeksu.|  
|`afEnableJITcompileTracking`|Wskazuje odpowiedniej wartości z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afDisableJITcompileOptimizer`|Wskazuje odpowiedniej wartości z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afRetargetable`|Wskazuje, czy zestaw można przekierować go w czasie wykonywania do zestawu od innego wydawcy.|  
|`afContentType_Mask`|Maska, który opisuje typ zawartości.|  
|`afContentType_Default`|Określa domyślny typ zawartości.|  
|`afContentType_WindowsRuntime`|Wskazuje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typ zawartości.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
