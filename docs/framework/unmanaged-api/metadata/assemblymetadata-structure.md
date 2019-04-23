---
title: ASSEMBLYMETADATA — Struktura
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f0a9b9c149c86b4d9121275aa858dfdc0cdbac7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195166"
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA — Struktura
Zawiera informacje o przywoływanego zestawu, w tym jej wersji oraz jego poziom wsparcia dla ustawień regionalnych, procesory i systemy operacyjne.  
  
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
|`usMajorVersion`|Główny numer wersji przywoływanego zestawu. Ta wartość nie może mieć wartość zero. Jeśli wszystkie bity `usMajorVersion` są ustawione, nie określono wersji głównej.|  
|`usMinorVersion`|Pomocniczy numer wersji przywoływanego zestawu. Ta wartość nie może mieć wartość zero. Jeśli wszystkie bity `usMinorVersion` są ustawione, wersja pomocnicza nie jest określony.|  
|`usBuildNumber`|Numer kompilacji przywoływanego zestawu. Ta wartość nie może mieć wartość zero. Jeśli wszystkie bity `usBuildNumber` są ustawione, nie podano numeru kompilacji.|  
|`usRevisionNumber`|Numer poprawki przywoływanego zestawu. Ta wartość nie może mieć wartość zero. Jeśli wszystkie bity `usRevisionNumber` są ustawione, numer wersji nie jest określony.|  
|`szLocale`|Lista nazw ustawień regionalnych, zgodne ze specyfikacją RFC1766, oddzielone średnikami, określanie ustawień regionalnych obsługiwanych przez zestaw z odwołania. Wartość zerowa wskazuje niezależność od ustawień regionalnych. **Uwaga:**  W .NET Framework w wersji 1.0, nie można określić kilka ustawień regionalnych.|  
|`cbLocale`|Rozmiar w znaków `szLocale`.|  
|`rdwProcessor`|Tablica identyfikatorów, zgodnie z definicją w pliku Winnt.h, dla typów procesora, które są obsługiwane przez zestaw z odwołania. Wartość NULL oznacza niezależność procesora.|  
|`ulProcessor`|Długość `rdwProcessor` tablicy.|  
|`rOS`|Tablica [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) wystąpień, określając systemów operacyjnych, które są obsługiwane przez zestaw z odwołania. Wartość NULL oznacza niezależność od systemu operacyjnego.|  
|`ulOS`|Długość `rOS` tablicy.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [OSINFO, struktura](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
