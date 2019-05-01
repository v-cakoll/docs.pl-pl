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
ms.openlocfilehash: 0aba49fb4a60b2e471c541a8d8531a1cbc8627f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775203"
---
# <a name="osinfo-structure"></a>OSINFO — Struktura
Zawiera szczegóły dotyczące systemu operacyjnego dla zestawu lub modułu.  
  
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
|`dwOSPlatformId`|Jedna z wartości identyfikatora zdefiniowane przez funkcję platformy Microsoft Windows `GetVersionEx`. Obsługiwane są następujące wartości:<br /><br /> -VER_PLATFORM_WIN32s, lub 0x0000, aby określić systemu Microsoft Windows 3.1.<br />-VER_PLATFORM_WIN32_WINDOWS, lub 0x0001, aby określić Windows 95, Windows 98 lub systemy operacyjne, które wywodzi się z nimi.<br />-VER_PLATFORM_WIN32_NT, lub 0x0010, aby określić Windows NT lub systemy operacyjne, które wywodzi się z niego.|  
|`dwOSMajorVersion`|Wersja główna systemu operacyjnego, lub wartość NULL, aby wskazać dowolną wersję.|  
|`dwOSMinorVersion`|Wersja pomocnicza systemu operacyjnego, lub wartość NULL, aby wskazać dowolną wersję.|  
  
## <a name="remarks"></a>Uwagi  
 `OSINFO` opiera się na `OSVERSIONINFOEX` struktury, to znaczy, używane wywołania funkcji platformy Microsoft Windows `GetVersionEx`. Ta struktura jest używany przez assemblymetadata — struktura w celu wskazania, jego obsługa systemu operacyjnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
