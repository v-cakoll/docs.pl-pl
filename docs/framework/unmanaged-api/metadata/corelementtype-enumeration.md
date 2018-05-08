---
title: CorElementType Enumeration1
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
ms.openlocfilehash: ebe2cf95f5637e6924b85c2389f1c59679580298
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corelementtype-enumeration1"></a>CorElementType Enumeration1
Określa środowisko uruchomieniowe języka wspólnego <xref:System.Type>, typ i/lub informacje o typie w podpisie typu metadanych.  
  
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
|`ELEMENT_TYPE_CHAR`|Typ znaków.|  
|`ELEMENT_TYPE_I1`|Całkowita 1-bajtowego.|  
|`ELEMENT_TYPE_U1`|Niepodpisane 1-bajtowych liczb całkowitych.|  
|`ELEMENT_TYPE_I2`|Całkowita 2-bajtowych.|  
|`ELEMENT_TYPE_U2`|2-bajtowa liczba całkowita bez znaku.|  
|`ELEMENT_TYPE_I4`|Całkowita 4-bajtowych.|  
|`ELEMENT_TYPE_U4`|4-bajtowa liczba całkowita bez znaku.|  
|`ELEMENT_TYPE_I8`|Całkowita 8-bajtowych.|  
|`ELEMENT_TYPE_U8`|8-bajtowa liczba całkowita bez znaku.|  
|`ELEMENT_TYPE_R4`|4-bajtowych zmiennoprzecinkowej.|  
|`ELEMENT_TYPE_R8`|8-bajtowych zmiennoprzecinkowych.|  
|`ELEMENT_TYPE_STRING`|Typem System.String.|  
|`ELEMENT_TYPE_PTR`|Modyfikator typu wskaźnika.|  
|`ELEMENT_TYPE_BYREF`|Modyfikator typu odwołania.|  
|`ELEMENT_TYPE_VALUETYPE`|Modyfikator typu wartości.|  
|`ELEMENT_TYPE_CLASS`|Modyfikator typu klasy.|  
|`ELEMENT_TYPE_VAR`|Modyfikator zmiennej typu klasy.|  
|`ELEMENT_TYPE_ARRAY`|Modyfikator typu tablicy wielowymiarowej.|  
|`ELEMENT_TYPE_GENERICINST`|Modyfikator typu typów ogólnych.|  
|`ELEMENT_TYPE_TYPEDBYREF`|Odniesienie typu.|  
|`ELEMENT_TYPE_I`|Rozmiar całkowitą natywnego.|  
|`ELEMENT_TYPE_U`|Rozmiar całkowitą bez znaku macierzystego.|  
|`ELEMENT_TYPE_FNPTR`|Wskaźnik do funkcji.|  
|`ELEMENT_TYPE_OBJECT`|Typ elementu System.Object.|  
|`ELEMENT_TYPE_SZARRAY`|Jednowymiarowe, zero modyfikator typu dolna granica tablicy.|  
|`ELEMENT_TYPE_MVAR`|Modyfikator zmiennej typu metody.|  
|`ELEMENT_TYPE_CMOD_REQD`|Modyfikator wymagane języka C.|  
|`ELEMENT_TYPE_CMOD_OPT`|Modyfikator opcjonalne języka C.|  
|`ELEMENT_TYPE_INTERNAL`|Używane wewnętrznie.|  
|`ELEMENT_TYPE_MAX`|Nieprawidłowy typ.|  
|`ELEMENT_TYPE_MODIFIER`|Używane wewnętrznie.|  
|`ELEMENT_TYPE_SENTINEL`|Modyfikator typu będącego wartownik listę zmiennych liczba parametrów.|  
|`ELEMENT_TYPE_PINNED`|Używane wewnętrznie.|  
  
## <a name="remarks"></a>Uwagi  
 Modyfikatory typu stanowią podstawę reprezentujący bardziej złożonych typów. A `CorElementType` typu modyfikator wartość jest stosowana do poniższą w podpisie typu wartości. Wartość, która wykonuje `CorElementType` wartość modyfikator typu może być `CorElementType` wartość typu prostego, token metadanych lub inna wartość określoną w poniższej tabeli.  
  
> [!NOTE]
>  Wszystkie numery (*numer*, *argument Count*, *token metadanych*, *rangę*, *liczby*i *powiązany*) są przechowywane w postaci skompresowanej liczb całkowitych. Zobacz [standardowe ECMA-335 - infrastruktury języka wspólnego (CLI)](http://go.microsoft.com/fwlink/?LinkID=116487) w witrynie sieci Web ECMA, aby uzyskać szczegółowe informacje.  
  
|Modyfikator typu|Format|  
|-------------------|------------|  
|`ELEMENT_TYPE_PTR`|Poprawności elementu ELEMENT_TYPE_PTR < `CorElementType` wartość >|  
|`ELEMENT_TYPE_BYREF`|ELEMENT_TYPE_BYREF < `CorElementType` wartość >|  
|`ELEMENT_TYPE_VALUETYPE`|ELEMENT_TYPE_VALUETYPE < `mdTypeDef` token metadanych >|  
|`ELEMENT_TYPE_CLASS`|Po elemencie ELEMENT_TYPE_CLASS < `mdTypeDef` token metadanych >|  
|`ELEMENT_TYPE_VAR`|ELEMENT_TYPE_VAR \<numer >|  
|`ELEMENT_TYPE_ARRAY`|ELEMENT_TYPE_ARRAY < `CorElementType` wartość > \<rangę > \<count1 > \<bound1 >... \<countN > \<boundN >|  
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST < `mdTypeDef` token metadanych > \<argument Count > \<arg1 >... \<argN >|  
|`ELEMENT_TYPE_FNPTR`|ELEMENT_TYPE_FNPTR \<pełną podpisu funkcji, łącznie z konwencji wywoływania >|  
|`ELEMENT_TYPE_SZARRAY`|ELEMENT_TYPE_SZARRAY < `CorElementType` wartość >|  
|`ELEMENT_TYPE_MVAR`|ELEMENT_TYPE_MVAR \<numer >|  
|`ELEMENT_TYPE_CMOD_REQD`|Element ELEMENT_TYPE_ < `mdTypeRef` lub `mdTypeDef` token metadanych >|  
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT < `mdTypeRef` lub `mdTypeDef` token metadanych >|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
