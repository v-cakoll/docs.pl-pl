---
title: ASSEMBLY_INFO — Struktura
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bae19ec18c54eccc7aa54d2d3a006f36ba8ab762
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110880"
---
# <a name="assemblyinfo-structure"></a>ASSEMBLY_INFO — Struktura
Zawiera informacje o zestawie, który jest zarejestrowany w globalnej pamięci podręcznej.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`cbAssemblyInfo`|Rozmiar w bajtach, struktury. To pole jest zarezerwowane dla przyszłej rozszerzalności.|  
|`dwAssemblyFlags`|Flagi wskazujące szczegółowe informacje dotyczące instalacji o zestawie. Obsługiwane są następujące wartości:<br /><br /> -ASSEMBLYINFO_FLAG_INSTALLED wartość, co oznacza, że zestaw jest zainstalowany. Zawsze ustawia dla bieżącej wersji programu .NET Framework `dwAssemblyFlags` tej wartości.<br />-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT wartość, co oznacza, że zestaw jest rezydentnego ładunku. Bieżąca wersja programu .NET Framework nigdy nie ustawia `dwAssemblyFlags` tej wartości.|  
|`uliAssemblySizeInKB`|Całkowity rozmiar w kilobajtach, plików, które zawiera zestaw.|  
|`pszCurrentAssemblyPathBuf`|Wskaźnik do buforu ciągu, który zawiera bieżącą ścieżkę do pliku manifestu. Ścieżka musi kończyć się znakiem null.|  
|`cchBuf`|Liczba znaków dwubajtowych, łącznie z terminatorem null, która `pszCurrentAssemblyPathBuf` zawiera.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie — Struktury](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [Global Assembly Cache](../../../../docs/framework/app-domains/gac.md)
