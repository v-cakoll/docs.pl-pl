---
title: CorTypeAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
ms.openlocfilehash: b6936081ca3dbadb4f802a6856fafb53f6cef3fa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008966"
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr — Wyliczenie
Zawiera wartości wskazujące metadane typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`tdVisibilityMask`|Służy do wyświetlania informacji o widoczności.|  
|`tdNotPublic`|Określa, że typ nie należy do zakresu publicznego.|  
|`tdPublic`|Określa, że typ znajduje się w zakresie publicznym.|  
|`tdNestedPublic`|Określa, że typ jest zagnieżdżony dla widoczności publicznej.|  
|`tdNestedPrivate`|Określa, że typ jest zagnieżdżony z widocznością prywatną.|  
|`tdNestedFamily`|Określa, że typ jest zagnieżdżony dla widoczności rodziny.|  
|`tdNestedAssembly`|Określa, że typ jest zagnieżdżony z widocznością zestawu.|  
|`tdNestedFamANDAssem`|Określa, że typ jest zagnieżdżony z rodziną i widocznością zestawu.|  
|`tdNestedFamORAssem`|Określa, że typ jest zagnieżdżony dla rodziny lub widoczności zestawu.|  
|`tdLayoutMask`|Pobiera informacje o układzie dla tego typu.|  
|`tdAutoLayout`|Określa, że pola tego typu są ustanawiane automatycznie.|  
|`tdSequentialLayout`|Określa, że pola tego typu są określane sekwencyjnie.|  
|`tdExplicitLayout`|Określa, że układ pola jest dostarczany jawnie.|  
|`tdClassSemanticsMask`|Pobiera informacje semantyczne o typie.|  
|`tdClass`|Określa, że typ jest klasą.|  
|`tdInterface`|Określa, że typ jest interfejsem.|  
|`tdAbstract`|Określa, że typ jest abstrakcyjny.|  
|`tdSealed`|Określa, że typ nie może zostać rozszerzony.|  
|`tdSpecialName`|Określa, że nazwa klasy jest specjalna. Jego nazwa opisuje sposób.|  
|`tdImport`|Określa, że typ jest importowany.|  
|`tdSerializable`|Określa, że typ jest możliwy do serializacji.|  
|`tdWindowsRuntime`|Określa, że ten typ jest typem środowisko wykonawcze systemu Windows.|  
|`tdStringFormatMask`|Pobiera informacje o sposobie kodowania i formatowania ciągów.|  
|`tdAnsiClass`|Określa, że ten typ interpretuje LPTSTR jako ANSI.|  
|`tdUnicodeClass`|Określa, że ten typ interpretuje LPTSTR jako Unicode.|  
|`tdAutoClass`|Określa, że ten typ interpretuje LPTSTR automatycznie.|  
|`tdCustomFormatClass`|Określa, że typ ma niestandardowe kodowanie określone przez `CustomFormatMask` .|  
|`tdCustomFormatMask`|Użyj tej maski, aby uzyskać informacje o niestandardowym kodowaniu dla natywnej międzyoperacyjności. Znaczenie wartości tych dwóch bitów nie jest określone.|  
|`tdBeforeFieldInit`|Określa, że typ musi być zainicjowany przed pierwszą próbą uzyskania dostępu do pola statycznego.|  
|`tdForwarder`|Określa, że typ jest eksportowany i usługa przesyłania dalej typu.|  
|`tdReservedMask`|Ta flaga i poniższe flagi są używane wewnętrznie przez środowisko uruchomieniowe języka wspólnego.|  
|`tdRTSpecialName`|Określa, że środowisko uruchomieniowe języka wspólnego powinno sprawdzać kodowanie nazw.|  
|`tdHasSecurity`|Określa, że typ ma skojarzone zabezpieczenia.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
