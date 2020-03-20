---
title: OSINFO — Struktura
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: 048fe687e4d979576896f5310bddc855b40bb695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175229"
---
# <a name="osinfo-structure"></a>OSINFO — Struktura
Zawiera szczegółowe informacje o systemie operacyjnym dla zestawu lub modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`dwOSPlatformId`|Jedna z wartości identyfikatorów zdefiniowanych przez `GetVersionEx`funkcję platformy Microsoft Windows . Obsługiwane są następujące wartości:<br /><br /> - VER_PLATFORM_WIN32s lub 0x0000, aby określić system Microsoft Windows 3.1.<br />- VER_PLATFORM_WIN32_WINDOWS lub 0x0001, aby określić Windows 95, Windows 98 lub systemów operacyjnych pochodzi od nich.<br />- VER_PLATFORM_WIN32_NT lub 0x0002, aby określić Windows NT lub systemów operacyjnych zstąpił od niego.|  
|`dwOSMajorVersion`|Wersja główna systemu operacyjnego lub wartość NULL wskazująca dowolną wersję.|  
|`dwOSMinorVersion`|Wersja pomocnicza systemu operacyjnego lub wartość NULL wskazująca dowolną wersję.|  
  
## <a name="remarks"></a>Uwagi  
 `OSINFO`opiera się `OSVERSIONINFOEX` na strukturze używanej w wywołaniach `GetVersionEx`funkcji platformy Microsoft Windows . Ta struktura jest używana przez assemblymetadata struktury, aby wskazać jego obsługi systemu operacyjnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Używany jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Struktury metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
