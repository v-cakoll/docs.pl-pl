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
ms.openlocfilehash: 9d6ec37bbd8750c27a41b5f18180c7726cdcd483
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442842"
---
# <a name="corassemblyflags-enumeration"></a>CorAssemblyFlags — Wyliczenie
Zawiera wartości, które opisują metadanych stosowane do kompilacji zestawu.  
  
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
|`afPA_MSIL`|Wskazuje, że architektura procesora jest obojętny (plikiem PE32).|  
|`afPA_x86`|Wskazuje, że architektura procesora jest x86 (plikiem PE32).|  
|`afPA_IA64`|Wskazuje, że architektura procesora jest Itanium (plikiem PE32 +).|  
|`afPA_AMD64`|Wskazuje, że architektura procesora jest AMD X64 (plikiem PE32 +).|  
|`afPA_ARM`|Wskazuje, że architektura procesora jest ARM (plikiem PE32).|  
|`afPA_NoPlatform`|Wskazuje, że zestaw jest zestaw odwołania; oznacza to stosuje się do dowolnej architekturze ale nie można uruchomić na dowolnej architekturze. W związku z tym flaga jest taka sama jak `afPA_Mask`.|  
|`afPA_Specified`|Wskazuje, że flagi architektury procesora powinien propagowane do `AssemblyRef` rekordu.|  
|`afPA_Mask`|Maski, który opisuje architektury procesora.|  
|`afPA_FullMask`|Określa, czy znajduje się opis architektury procesora.|  
|`afPA_Shift`|Wskazuje licznik przesunięć we flagach architektury procesora do i z indeksu.|  
|`afEnableJITcompileTracking`|Wskazuje wartość odpowiadająca z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afDisableJITcompileOptimizer`|Wskazuje wartość odpowiadająca z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afRetargetable`|Wskazuje, że zestaw cel może zostać zmieniony w czasie wykonywania do zestawu z innego wydawcę.|  
|`afContentType_Mask`|Maska, który opisuje typ zawartości.|  
|`afContentType_Default`|Określa domyślny typ zawartości.|  
|`afContentType_WindowsRuntime`|Wskazuje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typ zawartości.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
