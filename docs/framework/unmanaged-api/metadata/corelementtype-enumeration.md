---
title: CorElementType — Wyliczenie
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
ms.openlocfilehash: a4e9268d292004f447b30c82f1db4d0fe58404fe
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937950"
---
# <a name="corelementtype-enumeration"></a>CorElementType — Wyliczenie

Określa <xref:System.Type>środowiska uruchomieniowego języka wspólnego, modyfikator typu lub informacje o typie w sygnaturze typu metadanych.

## <a name="syntax"></a>Składnia

```cpp
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
|`ELEMENT_TYPE_BOOLEAN`|Typ wartości logicznej|
|`ELEMENT_TYPE_CHAR`|Typ znaku.|
|`ELEMENT_TYPE_I1`|1-bajtowa liczba całkowita ze znakiem.|
|`ELEMENT_TYPE_U1`|1-bajtowa liczba całkowita bez znaku.|
|`ELEMENT_TYPE_I2`|Podpisana 2-bajtowa liczba całkowita.|
|`ELEMENT_TYPE_U2`|2-bajtowa liczba całkowita bez znaku.|
|`ELEMENT_TYPE_I4`|Podpisana 4-bajtowa liczba całkowita.|
|`ELEMENT_TYPE_U4`|4-bajtowa liczba całkowita bez znaku.|
|`ELEMENT_TYPE_I8`|8-bajtowa liczba całkowita ze znakiem.|
|`ELEMENT_TYPE_U8`|8-bajtowa liczba całkowita bez znaku.|
|`ELEMENT_TYPE_R4`|4-bajtowy zmiennoprzecinkowy.|
|`ELEMENT_TYPE_R8`|8-bajtowy zmiennoprzecinkowy.|
|`ELEMENT_TYPE_STRING`|Typ System. String.|
|`ELEMENT_TYPE_PTR`|Modyfikator typu wskaźnika.|
|`ELEMENT_TYPE_BYREF`|Modyfikator typu odwołania.|
|`ELEMENT_TYPE_VALUETYPE`|Modyfikator typu wartości.|
|`ELEMENT_TYPE_CLASS`|Modyfikator typu klasy.|
|`ELEMENT_TYPE_VAR`|Modyfikator typu zmiennej klasy.|
|`ELEMENT_TYPE_ARRAY`|Modyfikator typu wielowymiarowej tablicy.|
|`ELEMENT_TYPE_GENERICINST`|Modyfikator typu dla typów ogólnych.|
|`ELEMENT_TYPE_TYPEDBYREF`|Wpisane odwołanie.|
|`ELEMENT_TYPE_I`|Rozmiar natywnej liczby całkowitej.|
|`ELEMENT_TYPE_U`|Rozmiar nieoznaczonej natywnej liczby całkowitej.|
|`ELEMENT_TYPE_FNPTR`|Wskaźnik do funkcji.|
|`ELEMENT_TYPE_OBJECT`|Typ elementu System. Object.|
|`ELEMENT_TYPE_SZARRAY`|Modyfikator typu tablicy jednowymiarowej o niższym poziomie.|
|`ELEMENT_TYPE_MVAR`|Modyfikator typu zmiennej metody.|
|`ELEMENT_TYPE_CMOD_REQD`|Modyfikator wymaganego języka C.|
|`ELEMENT_TYPE_CMOD_OPT`|Opcjonalny modyfikator języka C.|
|`ELEMENT_TYPE_INTERNAL`|Używane wewnętrznie.|
|`ELEMENT_TYPE_MAX`|Nieprawidłowy typ.|
|`ELEMENT_TYPE_MODIFIER`|Używane wewnętrznie.|
|`ELEMENT_TYPE_SENTINEL`|Modyfikator typu, który jest wskaźnikiem na listę zmiennej liczby parametrów.|
|`ELEMENT_TYPE_PINNED`|Używane wewnętrznie.|

## <a name="remarks"></a>Uwagi

Modyfikatory typu stanowią podstawę do reprezentowania bardziej złożonych typów. Wartość modyfikatora typu `CorElementType` jest stosowana do wartości, która bezpośrednio następuje w sygnaturze typu. Wartość, która następuje po wartości modyfikatora typu `CorElementType`, może być `CorElementType` wartością typu prostego, tokenem metadanych lub inną wartością, jak określono w poniższej tabeli.

> [!NOTE]
> Wszystkie liczby (*Liczba*, liczba *argumentów*, *token metadanych*, *ranga*, *Liczba*i *powiązana*) są przechowywane jako skompresowane liczby całkowite. Aby uzyskać szczegółowe informacje, zobacz [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) w witrynie sieci Web ECMA.

|Modyfikator typu|Format|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|ELEMENT_TYPE_PTR \<wartości `CorElementType` >|
|`ELEMENT_TYPE_BYREF`|ELEMENT_TYPE_BYREF \<wartości `CorElementType` >|
|`ELEMENT_TYPE_VALUETYPE`|ELEMENT_TYPE_VALUETYPE \<token `mdTypeDef` metadanych >|
|`ELEMENT_TYPE_CLASS`|ELEMENT_TYPE_CLASS \<token `mdTypeDef` metadanych >|
|`ELEMENT_TYPE_VAR`|Numer \<ELEMENT_TYPE_VAR >|
|`ELEMENT_TYPE_ARRAY`|ELEMENT_TYPE_ARRAY \<`CorElementType` wartości > \<rank > \<count1 > \<bound1 >... \<countN > \<boundN >|
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST \<token `mdTypeDef` metadanych > \<liczbę argumentów > \<arg1 >... \<argN >|
|`ELEMENT_TYPE_FNPTR`|ELEMENT_TYPE_FNPTR \<pełną sygnaturę funkcji, w tym konwencją wywoływania >|
|`ELEMENT_TYPE_SZARRAY`|ELEMENT_TYPE_SZARRAY \<wartości `CorElementType` >|
|`ELEMENT_TYPE_MVAR`|Numer \<ELEMENT_TYPE_MVAR >|
|`ELEMENT_TYPE_CMOD_REQD`|ELEMENT_TYPE_\<`mdTypeRef` lub `mdTypeDef` token metadanych >|
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT \<`mdTypeRef` lub `mdTypeDef` token metadanych >|

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** CorHdr. h

**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
