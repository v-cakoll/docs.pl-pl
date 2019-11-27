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
ms.openlocfilehash: 24ec1f7d553a59425f7eb02af8e91010d940eb07
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444266"
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA — Struktura
Zawiera informacje o zestawie, do którego istnieje odwołanie, w tym jego wersji oraz o poziomie wsparcia dla ustawień regionalnych, procesorów i systemów operacyjnych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`usMajorVersion`|Numer wersji głównej przywoływanego zestawu. Ta wartość nie może być równa zero. Jeśli wszystkie bity `usMajorVersion` są ustawione, wersja główna nie zostanie określona.|  
|`usMinorVersion`|Pomocniczy numer wersji przywoływanego zestawu. Ta wartość nie może być równa zero. Jeśli wszystkie bity `usMinorVersion` są ustawione, nie zostanie określona wersja pomocnicza.|  
|`usBuildNumber`|Numer kompilacji przywoływanego zestawu. Ta wartość nie może być równa zero. Jeśli wszystkie bity `usBuildNumber` są ustawione, numer kompilacji nie zostanie określony.|  
|`usRevisionNumber`|Numer poprawki przywoływanego zestawu. Ta wartość nie może być równa zero. Jeśli wszystkie bity `usRevisionNumber` są ustawione, numer poprawki nie zostanie określony.|  
|`szLocale`|Lista nazw ustawień regionalnych zgodna ze specyfikacją RFC1766, oddzielona średnikami, określająca wartości lokalne obsługiwane przez przywoływany zestaw. Wartość null wskazuje niezależność ustawień regionalnych. **Uwaga:**  W .NET Framework w wersji 1,0 nie można określić więcej niż jednego ustawienia regionalnego.|  
|`cbLocale`|Rozmiar w szerokich znakach `szLocale`.|  
|`rdwProcessor`|Tablica identyfikatorów, zgodnie z definicją w Winnt. h, dla typów procesorów obsługiwanych przez przywoływany zestaw. Wartość NULL wskazuje niezależność procesora.|  
|`ulProcessor`|Długość tablicy `rdwProcessor`.|  
|`rOS`|Tablica wystąpień [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) określających systemy operacyjne, które są obsługiwane przez przywoływany zestaw. Wartość NULL wskazuje niezależność systemu operacyjnego.|  
|`ulOS`|Długość tablicy `rOS`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [OSINFO, struktura](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
