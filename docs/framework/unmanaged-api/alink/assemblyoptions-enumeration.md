---
title: "AssemblyOptions — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyOptions
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ccbbcabd3fbb372322ca6334f6ab6db4fdafc2f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions — Wyliczenie
Wylicza opcje zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|optAssemOS|Parametry - zakodowane jako: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".|  
|optAssemProcessor|ULONG|  
|optAssemLocale|String — zawiera zestaw ustawień regionalnych.|  
|optAssemVersion|Parametry - zakodowane jako: "Główna.pomocnicza.kompilacja.poprawka".|  
|optAssemCompany|String — zawiera firmy.|  
|optAssemProduct|String — zawiera nazwę produktu.|  
|optAssemProductVersion|Ciąg (znanej także jako InformationalVersion).|  
|optAssemCopyright|String — zawiera informacje o prawach autorskich.|  
|optAssemTrademark|String — zawiera informacje o znakach towarowych.|  
|optAssemKeyFile|String (nazwa pliku).|  
|optAssemKeyName|String (nazwa klucza).|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Wartość logiczna (określane również jako DelaySign).|  
|optAssemFileVersion|Parametry - zakodowane jako "Główna.pomocnicza.kompilacja.poprawka"--identyczny ProductVersion.|  
|optAssemSatelliteVer|Parametry - zakodowane jako "Główna.pomocnicza.kompilacja.poprawka".|  
|optLastAssemOption|Licznik liczby elementów.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** alink.h  
  
 **Biblioteka**: alink.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Al.exe (konsolidator zestawów)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
