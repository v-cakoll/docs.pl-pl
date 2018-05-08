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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c5bc63da7ebe86b653c9bef7caeb1cf28d3a7f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="osinfo-structure"></a>OSINFO — Struktura
Zawiera szczegółowe informacje dotyczące systemu operacyjnego dla zestawu lub modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`dwOSPlatformId`|Jedna z wartości identyfikator zdefiniowany przez funkcję platform Microsoft Windows `GetVersionEx`. Obsługiwane są następujące wartości:<br /><br /> -VER_PLATFORM_WIN32s, lub 0x0000, aby określić Microsoft Windows 3.1.<br />-VER_PLATFORM_WIN32_WINDOWS, lub 0x0001, aby określić Windows 95, Windows 98 lub systemów operacyjnych podrzędne w stosunku do nich.<br />-VER_PLATFORM_WIN32_NT, lub 0x0010, do określenia systemu Windows NT lub podrzędne w stosunku do jego systemów operacyjnych.|  
|`dwOSMajorVersion`|Wersja główna systemu operacyjnego, lub wartość NULL, aby wskazać dowolnej wersji.|  
|`dwOSMinorVersion`|Wersja pomocnicza systemu operacyjnego, lub wartość NULL, aby wskazać dowolnej wersji.|  
  
## <a name="remarks"></a>Uwagi  
 `OSINFO` jest oparta na `OSVERSIONINFOEX` struktury który jest używany w wywołań funkcji platform Microsoft Windows `GetVersionEx`. Ta struktura jest używany przez assemblymetadata — struktura w celu wskazania jego obsługę systemu operacyjnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
