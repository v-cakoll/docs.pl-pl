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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f65c2f74ec5efda027d90b3ffda9a5da5c239122
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025715"
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr — Wyliczenie
Zawiera wartości, które wskazują metadanych typu.  
  
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
|`tdVisibilityMask`|Używane, aby uzyskać informacje o widoczności typu.|  
|`tdNotPublic`|Określa, że typ nie jest w zakresie publicznych.|  
|`tdPublic`|Określa, że typ znajduje się w zakresie publicznych.|  
|`tdNestedPublic`|Określa, że typ jest zagnieżdżona publicznych wgląd.|  
|`tdNestedPrivate`|Określa, że typ jest zagnieżdżona prywatnej wgląd.|  
|`tdNestedFamily`|Określa, że typ jest zagnieżdżona o widoczności rodziny.|  
|`tdNestedAssembly`|Określa, że typ jest zagnieżdżona z widocznością zestawu.|  
|`tdNestedFamANDAssem`|Określa, że typ jest zagnieżdżona o widoczności Rodzina i zestaw.|  
|`tdNestedFamORAssem`|Określa, że typ jest zagnieżdżona o widoczności Rodzina lub zestaw.|  
|`tdLayoutMask`|Pobiera informacje o układzie dla typu.|  
|`tdAutoLayout`|Określa, że pola tego typu są ułożone w automatycznie.|  
|`tdSequentialLayout`|Określa, że pola tego typu są ułożone w sekwencyjnie.|  
|`tdExplicitLayout`|Określa, że układ tego pola jest jawnie podana.|  
|`tdClassSemanticsMask`|Pobiera semantycznego informacje o typie.|  
|`tdClass`|Określa, że typ jest klasą.|  
|`tdInterface`|Określa, że typ jest interfejsem.|  
|`tdAbstract`|Określa, że typ jest abstrakcyjny.|  
|`tdSealed`|Określa, że typ nie może zostać rozszerzony.|  
|`tdSpecialName`|Określa, że nazwa klasy jest specjalne. Nazwy w tym artykule opisano sposób.|  
|`tdImport`|Określa, że typ jest importowany.|  
|`tdSerializable`|Określa, czy jest możliwy do serializacji.|  
|`tdWindowsRuntime`|Określa, że ten typ jest typem środowiska wykonawczego Windows.|  
|`tdStringFormatMask`|Pobiera informacje dotyczące sposobu kodowany i sformatowane ciągi.|  
|`tdAnsiClass`|Określa, że ten typ interpretuje LPTSTR jako ANSI.|  
|`tdUnicodeClass`|Określa, że ten typ interpretuje LPTSTR jako Unicode.|  
|`tdAutoClass`|Określa, że ten typ interpretuje LPTSTR automatycznie.|  
|`tdCustomFormatClass`|Określa, że typ ma niestandardowych kodowanie określone przez `CustomFormatMask`.|  
|`tdCustomFormatMask`|Użyj tę maskę, aby pobrać niestandardowych informacji kodowania dla współdziałania z natywnego. Znaczenie wartości te dwa bity jest nieokreślona.|  
|`tdBeforeFieldInit`|Określa, że typ musi zostać zainicjowany przed pierwsza próba dostępu do pola statyczne.|  
|`tdForwarder`|Określa, że typ jest eksportowany, a typ usługi przesyłania dalej.|  
|`tdReservedMask`|Ta flaga i flagi poniżej są używane wewnętrznie przez środowisko uruchomieniowe języka wspólnego.|  
|`tdRTSpecialName`|Określa, że środowisko uruchomieniowe języka wspólnego ma sprawdzać, nazwa, kodowanie.|  
|`tdHasSecurity`|Określa, że typ ma zabezpieczeń skojarzonych z nim.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
