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
ms.openlocfilehash: d66e9bc3a027610d917e15dc9769b92ea1c5fb71
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345600"
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
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`dwOSPlatformId`|Jedna z wartości identyfikatora zdefiniowanych przez funkcję platformy Microsoft Windows `GetVersionEx`. Obsługiwane są następujące wartości:<br /><br /> -VER_PLATFORM_WIN32s lub 0x0000, aby określić system Microsoft Windows 3,1.<br />-VER_PLATFORM_WIN32_WINDOWS lub 0x0001, aby określić z nich systemy Windows 95, Windows 98 lub systemu operacyjnego.<br />-VER_PLATFORM_WIN32_NT lub 0x0002, aby określić system Windows NT lub systemy operacyjne, które są od niego podrzędne.|  
|`dwOSMajorVersion`|Wersja główna systemu operacyjnego lub wartość zerowa wskazująca dowolną wersję.|  
|`dwOSMinorVersion`|Wersja pomocnicza systemu operacyjnego lub wartość zerowa wskazująca dowolną wersję.|  
  
## <a name="remarks"></a>Uwagi  
 `OSINFO` jest oparty na strukturze `OSVERSIONINFOEX`, która jest używana w wywołaniach funkcji platformy Microsoft Windows `GetVersionEx`. Ta struktura jest używana przez strukturę ASSEMBLYMETADATA, aby wskazać jej obsługę systemu operacyjnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
