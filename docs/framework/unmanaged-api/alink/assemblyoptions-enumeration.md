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
ms.openlocfilehash: 324e30f6cbcaa1d1d81c7c03967dbb629d2cd6e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742267"
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
|optAssemDescription|String — zawiera opis zestawu.|  
|optAssemConfig|String — zawiera konfigurację zestawu.|  
|optAssemOS|Parametry - zakodowanymi w formacie: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".|  
|optAssemProcessor|ULONG|  
|optAssemLocale|String — zawiera zestaw ustawień regionalnych.|  
|optAssemVersion|Parametry - zakodowanymi w formacie: "Główna.pomocnicza.kompilacja.poprawka".|  
|optAssemCompany|String — zawiera firmy.|  
|optAssemProduct|String — zawiera nazwę produktu.|  
|optAssemProductVersion|Ciąg (znany także jako InformationalVersion).|  
|optAssemCopyright|String — zawiera informacje o prawach autorskich.|  
|optAssemTrademark|String — zawiera informacje o znakach towarowych.|  
|optAssemKeyFile|String (nazwa pliku).|  
|optAssemKeyName|Ciąg (nazwa klucza).|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Wartość logiczna (określana także jako DelaySign).|  
|optAssemFileVersion|Parametry - zakodowanymi w formacie "Główna.pomocnicza.kompilacja.poprawka"--takie same jak ProductVersion.|  
|optAssemSatelliteVer|Parametry - zakodowanymi w formacie "Główna.pomocnicza.kompilacja.poprawka".|  
|optLastAssemOption|Licznik liczby elementów.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** alink.h  
  
 **Biblioteka**: alink.dll  
  
## <a name="see-also"></a>Zobacz także

- [Al.exe (konsolidator zestawów)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
