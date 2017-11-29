---
title: "CorTypeAttr — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorTypeAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorTypeAttr
helpviewer_keywords: CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ab9ce555406dfeb16f99601e6b88af2395c91ae0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr — Wyliczenie
Zawiera wartości, które wskazuje typ metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`tdVisibilityMask`|Używać dla informacji o typie widoczności.|  
|`tdNotPublic`|Określa, że typ nie jest w zakresie publicznego.|  
|`tdPublic`|Określa, czy ten typ jest publiczny zakresu.|  
|`tdNestedPublic`|Określa, że typ jest zagnieżdżony z widoczności publicznej.|  
|`tdNestedPrivate`|Określa, że typ jest zagnieżdżony z widoczności prywatnej.|  
|`tdNestedFamily`|Określa, że typ jest zagnieżdżony z rodziny widoczności.|  
|`tdNestedAssembly`|Określa, że typ jest zagnieżdżony z widoczność zestawu.|  
|`tdNestedFamANDAssem`|Określa, że typ jest zagnieżdżony z widocznością rodziny i zestawu.|  
|`tdNestedFamORAssem`|Określa, że typ jest zagnieżdżony z widocznością rodziny lub zestawu.|  
|`tdLayoutMask`|Pobiera informacje o układzie dla typu.|  
|`tdAutoLayout`|Określa, że pola tego typu są automatycznie układu.|  
|`tdSequentialLayout`|Określa, że pola tego typu układ sekwencyjnie.|  
|`tdExplicitLayout`|Określa, że jest dostarczana układ tego pola.|  
|`tdClassSemanticsMask`|Pobiera informacje semantyczne o typie.|  
|`tdClass`|Określa, że typ jest klasą.|  
|`tdInterface`|Określa, czy ten typ jest interfejsem.|  
|`tdAbstract`|Określa, że typ jest abstrakcyjny.|  
|`tdSealed`|Określa, że typ nie może zostać rozszerzony.|  
|`tdSpecialName`|Określa, że nazwa klasy jest specjalne. Jego nazwa opisuje sposób.|  
|`tdImport`|Określa, że typ jest zaimportowany.|  
|`tdSerializable`|Określa, czy ten typ jest możliwy do serializacji.|  
|`tdWindowsRuntime`|Określa, że ten typ jest [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typu.|  
|`tdStringFormatMask`|Pobiera informacje o sposób kodowania i sformatowany ciągów.|  
|`tdAnsiClass`|Określa, że ten typ interpretacji LPTSTR jako ANSI.|  
|`tdUnicodeClass`|Określa, że ten typ interpretacji LPTSTR jako Unicode.|  
|`tdAutoClass`|Określa, że ten typ interpretacji LPTSTR automatycznie.|  
|`tdCustomFormatClass`|Określa, że typ ma niestandardowy kodowania, zgodnie z określonym `CustomFormatMask`.|  
|`tdCustomFormatMask`|Użyj tę maskę, aby pobrać niestandardowych informacji kodowania dla międzyoperacyjności z modelem natywnego. Znaczenie tej wartości te dwie usługi BITS jest nieokreślony.|  
|`tdBeforeFieldInit`|Określa, że typ musi zostać zainicjowany przed pierwsza próba uzyskania dostępu do statycznego pola.|  
|`tdForwarder`|Określa, że typ jest eksportowany, a usługi przesyłania dalej typu.|  
|`tdReservedMask`|Ta flaga i flagi poniżej są używane wewnętrznie przez środowisko uruchomieniowe języka wspólnego.|  
|`tdRTSpecialName`|Określa, że środowisko uruchomieniowe języka wspólnego ma sprawdzać kodowanie nazwy.|  
|`tdHasSecurity`|Określa, że typ ma zabezpieczeń skojarzonych z nim.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
