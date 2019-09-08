---
title: AssemblyOptions — Wyliczenie
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 49e7b73559e8def890f8df8f596fbe8ad5bb5d3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777481"
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions — Wyliczenie
Wylicza opcje zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a>Pola  
  
|Pole|Opis|  
|-----------|-----------------|  
|optAssemTitle|String — reprezentuje tytuł zestawu.|  
|optAssemDescription|Ciąg — zawiera opis zestawu.|  
|optAssemConfig|String — zawiera konfigurację zestawu.|  
|optAssemOS|Zakodowany ciąg jako: "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion".|  
|optAssemProcessor|ULONG|  
|optAssemLocale|Ciąg — zawiera ustawienia regionalne zestawu.|  
|optAssemVersion|Zakodowany ciąg jako: "Główna. pomocnicza. kompilacja. poprawka".|  
|optAssemCompany|Ciąg — zawiera firmę.|  
|optAssemProduct|String — zawiera nazwę produktu.|  
|optAssemProductVersion|Ciąg (znany również jako InformationalVersion).|  
|optAssemCopyright|Ciąg — zawiera informacje o prawach autorskich.|  
|optAssemTrademark|Ciąg — zawiera informacje o znakach towarowych.|  
|optAssemKeyFile|Ciąg (nazwa pliku).|  
|optAssemKeyName|Ciąg (nazwa klucza).|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (znany również jako DelaySign).|  
|optAssemFileVersion|Zakodowana ciągowo jako "główna. pomocnicza. kompilacja. poprawka" — taka sama jak ProductVersion.|  
|optAssemSatelliteVer|Kodowanie ciągu jako "główna. pomocnicza. kompilacja. poprawka".|  
|optLastAssemOption|Licznik liczby elementów.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** Alink. h  
  
 **Biblioteka**: Alink. dll  
  
## <a name="see-also"></a>Zobacz także

- [Al.exe (konsolidator zestawów)](../../tools/al-exe-assembly-linker.md)
