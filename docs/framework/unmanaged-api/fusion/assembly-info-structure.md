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
ms.openlocfilehash: a43d5e15c02a97ff10a6a5afd439cadebb6b33d2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109213"
---
# <a name="assembly_info-structure"></a>ASSEMBLY_INFO — Struktura
Zawiera informacje dotyczące zestawu, który jest zarejestrowany w globalnej pamięci podręcznej zestawów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`cbAssemblyInfo`|Rozmiar (w bajtach) struktury. To pole jest zarezerwowane do użytku w przyszłości.|  
|`dwAssemblyFlags`|Flagi wskazujące szczegóły instalacji zestawu. Obsługiwane są następujące wartości:<br /><br /> -Wartość ASSEMBLYINFO_FLAG_INSTALLED, która wskazuje, że zestaw jest zainstalowany. Bieżąca wersja .NET Framework zawsze ustawia `dwAssemblyFlags` na tę wartość.<br />-Wartość ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, która wskazuje, że zestaw jest rezydentem ładunku. Bieżąca wersja .NET Framework nigdy nie ustawia `dwAssemblyFlags` na tę wartość.|  
|`uliAssemblySizeInKB`|Łączny rozmiar (w kilobajtach) plików, które zawiera zestaw.|  
|`pszCurrentAssemblyPathBuf`|Wskaźnik do buforu ciągu, który przechowuje bieżącą ścieżkę do pliku manifestu. Ścieżka musi kończyć się znakiem null.|  
|`cchBuf`|Liczba znaków dwubajtowych, łącznie z terminatorem wartości null, który `pszCurrentAssemblyPathBuf` zawiera.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie — struktury](fusion-structures.md)
- [Global Assembly Cache](../../app-domains/gac.md)
