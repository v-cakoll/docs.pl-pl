---
title: "ASSEMBLYMETADATA — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 819510c14bd67e7fcc739a19ea945f16b2a66c9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA — Struktura
Zawiera informacje o przywoływanego zestawu, w tym jego wersja i poziomu wsparcia dla ustawień regionalnych, procesory i systemy operacyjne.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`usMajorVersion`|Numer wersji głównej przywoływanego zestawu. Ta wartość nie może wynosić zero. Jeśli wszystkie bity `usMajorVersion` są ustawione, nie określono wersji głównej.|  
|`usMinorVersion`|Numer wersji pomocniczej przywoływanego zestawu. Ta wartość nie może wynosić zero. Jeśli wszystkie bity `usMinorVersion` są ustawione, wersja pomocnicza nie jest określony.|  
|`usBuildNumber`|Numer kompilacji przywoływanego zestawu. Ta wartość nie może wynosić zero. Jeśli wszystkie bity `usBuildNumber` są ustawione, nie określono numeru kompilacji.|  
|`usRevisionNumber`|Numer poprawki przywoływanego zestawu. Ta wartość nie może wynosić zero. Jeśli wszystkie bity `usRevisionNumber` są ustawione, numer wersji nie jest określony.|  
|`szLocale`|Lista nazw ustawień regionalnych zgodne ze specyfikacją RFC1766, oddzielone średnikami, określając ustawienia regionalne obsługiwane przez zestaw z odwołania. Wartość null oznacza niezależność od ustawień regionalnych. **Uwaga:** w programie .NET Framework w wersji 1.0 nie można określić więcej niż jeden ustawień regionalnych.|  
|`cbLocale`|Rozmiar w znaki dwubajtowe `szLocale`.|  
|`rdwProcessor`|Tablica identyfikatorów, zgodnie z definicją w pliku Winnt.h, typy procesora, które są obsługiwane przez zestaw z odwołania. Wartości NULL wskazuje niezależność procesora.|  
|`ulProcessor`|Długość `rdwProcessor` tablicy.|  
|`rOS`|Tablica [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) wystąpień określenie systemów operacyjnych, które są obsługiwane przez zestaw z odwołania. Wartości NULL wskazuje niezależność od systemu operacyjnego.|  
|`ulOS`|Długość `rOS` tablicy.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [OSINFO, struktura](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
