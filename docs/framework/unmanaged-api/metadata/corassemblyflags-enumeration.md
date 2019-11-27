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
ms.openlocfilehash: fda890cee5f513ea8cf7e82e710f5451a860c49f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443913"
---
# <a name="corassemblyflags-enumeration"></a>CorAssemblyFlags — Wyliczenie
Zawiera wartości opisujące metadane zastosowane do kompilacji zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="members"></a>Members  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`afPublicKey`|Wskazuje, że odwołanie do zestawu zawiera pełny, niezmieszany klucz publiczny.|  
|`afPA_None`|Wskazuje, że nie określono architektury procesora.|  
|`afPA_MSIL`|Wskazuje, że architektura procesora jest neutralna (PE32).|  
|`afPA_x86`|Wskazuje, że architektura procesora to x86 (PE32).|  
|`afPA_IA64`|Wskazuje, że architektura procesora jest Itanium (PE32 +).|  
|`afPA_AMD64`|Wskazuje, że architektura procesora to AMD x64 (PE32 +).|  
|`afPA_ARM`|Wskazuje, że architektura procesora to ARM (PE32).|  
|`afPA_NoPlatform`|Wskazuje, że zestaw jest zestawem referencyjnym; oznacza to, że ma zastosowanie do dowolnej architektury, ale nie może działać w żadnej architekturze. W tym celu flaga jest taka sama jak `afPA_Mask`.|  
|`afPA_Specified`|Wskazuje, że flagi architektury procesora powinny być propagowane do rekordu `AssemblyRef`.|  
|`afPA_Mask`|Maska opisująca architekturę procesora.|  
|`afPA_FullMask`|Określa, że opis architektury procesora jest uwzględniany.|  
|`afPA_Shift`|Wskazuje liczbę przesunięć w flagach architektury procesora do i z indeksu.|  
|`afEnableJITcompileTracking`|Wskazuje odpowiednią wartość z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afDisableJITcompileOptimizer`|Wskazuje odpowiednią wartość z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afRetargetable`|Wskazuje, że zestaw można przekierować w czasie wykonywania do zestawu z innego wydawcy.|  
|`afContentType_Mask`|Maska opisująca typ zawartości.|  
|`afContentType_Default`|Wskazuje domyślny typ zawartości.|  
|`afContentType_WindowsRuntime`|Wskazuje typ zawartości środowisko wykonawcze systemu Windows.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
