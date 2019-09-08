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
ms.openlocfilehash: 390ab4881396bbc01337d087f05b6066153bfed1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795488"
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
|`dwAssemblyFlags`|Flagi wskazujące szczegóły instalacji zestawu. Obsługiwane są następujące wartości:<br /><br /> -Wartość ASSEMBLYINFO_FLAG_INSTALLED, która wskazuje, że zestaw jest zainstalowany. Bieżąca wersja .NET Framework zawsze jest ustawiana `dwAssemblyFlags` na tę wartość.<br />-Wartość ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, która wskazuje, że zestaw jest rezydentem ładunku. Bieżąca wersja .NET Framework nigdy nie ustawia `dwAssemblyFlags` tej wartości.|  
|`uliAssemblySizeInKB`|Łączny rozmiar (w kilobajtach) plików, które zawiera zestaw.|  
|`pszCurrentAssemblyPathBuf`|Wskaźnik do buforu ciągu, który przechowuje bieżącą ścieżkę do pliku manifestu. Ścieżka musi kończyć się znakiem null.|  
|`cchBuf`|Liczba znaków dwubajtowych, łącznie z terminatorem wartości null `pszCurrentAssemblyPathBuf` , który zawiera.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie — struktury](fusion-structures.md)
- [Global Assembly Cache](../../app-domains/gac.md)
