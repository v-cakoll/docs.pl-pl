---
title: CorElementType, wyliczenie1
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5112c3c8d5fef6efada4bffdfa575716503515e6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562553"
---
# <a name="corelementtype-enumeration1"></a>CorElementType, wyliczenie1
Określa środowisko uruchomieniowe języka wspólnego <xref:System.Type>, modyfikatora typu lub informacje o typie w podpisie typ metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorElementType {  
    ELEMENT_TYPE_END            = 0x0,  
    ELEMENT_TYPE_VOID           = 0x1,  
    ELEMENT_TYPE_BOOLEAN        = 0x2,  
    ELEMENT_TYPE_CHAR           = 0x3,  
    ELEMENT_TYPE_I1             = 0x4,  
    ELEMENT_TYPE_U1             = 0x5,  
    ELEMENT_TYPE_I2             = 0x6,  
    ELEMENT_TYPE_U2             = 0x7,  
    ELEMENT_TYPE_I4             = 0x8,  
    ELEMENT_TYPE_U4             = 0x9,  
    ELEMENT_TYPE_I8             = 0xa,  
    ELEMENT_TYPE_U8             = 0xb,  
    ELEMENT_TYPE_R4             = 0xc,  
    ELEMENT_TYPE_R8             = 0xd,  
    ELEMENT_TYPE_STRING         = 0xe,  
  
    ELEMENT_TYPE_PTR            = 0xf,  
    ELEMENT_TYPE_BYREF          = 0x10,  
  
    ELEMENT_TYPE_VALUETYPE      = 0x11,  
    ELEMENT_TYPE_CLASS          = 0x12,  
    ELEMENT_TYPE_VAR            = 0x13,  
    ELEMENT_TYPE_ARRAY          = 0x14,  
    ELEMENT_TYPE_GENERICINST    = 0x15,  
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,  
  
    ELEMENT_TYPE_I              = 0x18,  
    ELEMENT_TYPE_U              = 0x19,  
    ELEMENT_TYPE_FNPTR          = 0x1B,  
    ELEMENT_TYPE_OBJECT         = 0x1C,  
    ELEMENT_TYPE_SZARRAY        = 0x1D,  
    ELEMENT_TYPE_MVAR           = 0x1e,  
  
    ELEMENT_TYPE_CMOD_REQD      = 0x1F,  
    ELEMENT_TYPE_CMOD_OPT       = 0x20,  
  
    ELEMENT_TYPE_INTERNAL       = 0x21,  
    ELEMENT_TYPE_MAX            = 0x22,  
  
    ELEMENT_TYPE_MODIFIER       = 0x40,  
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,  
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER  
  
} CorElementType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ELEMENT_TYPE_END`|Używane wewnętrznie.|  
|`ELEMENT_TYPE_VOID`|Typ void.|  
|`ELEMENT_TYPE_BOOLEAN`|Typ Boolean|  
|`ELEMENT_TYPE_CHAR`|Typ znaku.|  
|`ELEMENT_TYPE_I1`|Całkowita 1-bajtowe.|  
|`ELEMENT_TYPE_U1`|1-bajtowe liczba całkowita bez znaku.|  
|`ELEMENT_TYPE_I2`|Całkowita 2-bajtowych.|  
|`ELEMENT_TYPE_U2`|2-bajtowa liczba całkowita bez znaku.|  
|`ELEMENT_TYPE_I4`|Całkowita 4-bajtowe.|  
|`ELEMENT_TYPE_U4`|4-bajtowa liczba całkowita bez znaku.|  
|`ELEMENT_TYPE_I8`|Całkowita 8 bajtów.|  
|`ELEMENT_TYPE_U8`|8-bajtowa liczba całkowita bez znaku.|  
|`ELEMENT_TYPE_R4`|4-bajtowych zmiennoprzecinkowej.|  
|`ELEMENT_TYPE_R8`|8-bajtowych zmiennoprzecinkowych.|  
|`ELEMENT_TYPE_STRING`|Typ System.String.|  
|`ELEMENT_TYPE_PTR`|Modyfikatora typu wskaźnika.|  
|`ELEMENT_TYPE_BYREF`|Modyfikatora typu odwołania.|  
|`ELEMENT_TYPE_VALUETYPE`|Wartości modyfikatora typu.|  
|`ELEMENT_TYPE_CLASS`|Modyfikator typu klasy.|  
|`ELEMENT_TYPE_VAR`|Modyfikator typu zmiennej klasy.|  
|`ELEMENT_TYPE_ARRAY`|Modyfikatora typu tablicy wielowymiarowej.|  
|`ELEMENT_TYPE_GENERICINST`|Modyfikatora typu dla typów ogólnych.|  
|`ELEMENT_TYPE_TYPEDBYREF`|Wpisane odwołania.|  
|`ELEMENT_TYPE_I`|Rozmiar natywnego liczby całkowitej.|  
|`ELEMENT_TYPE_U`|Rozmiar natywnego całkowitą bez znaku.|  
|`ELEMENT_TYPE_FNPTR`|Wskaźnik do funkcji.|  
|`ELEMENT_TYPE_OBJECT`|Typu System.Object.|  
|`ELEMENT_TYPE_SZARRAY`|Jednowymiarowe, zerowego modyfikatora typu dolną granicę tablicy.|  
|`ELEMENT_TYPE_MVAR`|Modyfikator typu zmiennej metody.|  
|`ELEMENT_TYPE_CMOD_REQD`|Język C wymaga modyfikator.|  
|`ELEMENT_TYPE_CMOD_OPT`|Modyfikator opcjonalne języka C.|  
|`ELEMENT_TYPE_INTERNAL`|Używane wewnętrznie.|  
|`ELEMENT_TYPE_MAX`|Nieprawidłowy typ.|  
|`ELEMENT_TYPE_MODIFIER`|Używane wewnętrznie.|  
|`ELEMENT_TYPE_SENTINEL`|Modyfikator typu, będącego wartownik listę zmienną liczbę parametrów.|  
|`ELEMENT_TYPE_PINNED`|Używane wewnętrznie.|  
  
## <a name="remarks"></a>Uwagi  
 Typy modyfikatorów stanowią podstawę dla bardziej złożonych typów reprezentujący. A `CorElementType` wartość modyfikator typu jest stosowany do wartości, który poprzedza w podpisie typu. Wartość, która następuje po `CorElementType` wartość modyfikator typu mogą być `CorElementType` wartość typu prostego, token metadanych lub inna wartość, jak to określono w poniższej tabeli.  
  
> [!NOTE]
>  Wszystkie numery (*numer*, *argument liczba*, *token metadanych*, *ranga*, *liczba*i *powiązany*) są przechowywane w postaci liczb całkowitych skompresowany. Zobacz [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) w witrynie sieci Web ECMA, aby uzyskać szczegółowe informacje.  
  
|Modyfikator typu|Format|  
|-------------------|------------|  
|`ELEMENT_TYPE_PTR`|ELEMENT_TYPE_PTR < `CorElementType` wartość >|  
|`ELEMENT_TYPE_BYREF`|Pole < `CorElementType` wartość >|  
|`ELEMENT_TYPE_VALUETYPE`|ELEMENT_TYPE_VALUETYPE < `mdTypeDef` token metadanych >|  
|`ELEMENT_TYPE_CLASS`|ELEMENT_TYPE_CLASS < `mdTypeDef` token metadanych >|  
|`ELEMENT_TYPE_VAR`|ELEMENT_TYPE_VAR \<numer >|  
|`ELEMENT_TYPE_ARRAY`|ELEMENT_TYPE_ARRAY < `CorElementType` wartość > \<ranga > \<count1 > \<bound1 >... \<countN > \<boundN >|  
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST < `mdTypeDef` token metadanych > \<argument liczby > \<arg1 >... \<argN >|  
|`ELEMENT_TYPE_FNPTR`|ELEMENT_TYPE_FNPTR \<pełny podpis dla funkcji, łącznie z konwencji wywoływania >|  
|`ELEMENT_TYPE_SZARRAY`|ELEMENT_TYPE_SZARRAY < `CorElementType` wartość >|  
|`ELEMENT_TYPE_MVAR`|ELEMENT_TYPE_MVAR \<numer >|  
|`ELEMENT_TYPE_CMOD_REQD`|Element ELEMENT_TYPE_ < `mdTypeRef` lub `mdTypeDef` token metadanych >|  
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT < `mdTypeRef` lub `mdTypeDef` token metadanych >|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** sekcję CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
