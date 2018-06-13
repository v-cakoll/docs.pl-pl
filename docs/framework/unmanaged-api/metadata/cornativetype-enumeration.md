---
title: CorNativeType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b28fe8e8fd8b602a01b6358f46f60cdf792ced0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448628"
---
# <a name="cornativetype-enumeration"></a>CorNativeType — Wyliczenie
Zawiera wartości, które opisują typy natywne niezarządzane.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,   
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|Nieaktualne.|  
|`NATIVE_TYPE_VOID`|Nieaktualne.|  
|`NATIVE_TYPE_BOOLEAN`|Wartość logiczna 4-bajtowych, gdzie wartość TRUE jest różna od zera i FALSE wynosi zero.|  
|`NATIVE_TYPE_I1`|Wartość całkowita 8-bitowa.|  
|`NATIVE_TYPE_U1`|Niepodpisane 8-bitową liczbę całkowitą.|  
|`NATIVE_TYPE_I2`|Wartość całkowita 16-bitowych.|  
|`NATIVE_TYPE_U2`|Niepodpisane 16-bitową liczbę całkowitą.|  
|`NATIVE_TYPE_I4`|Wartość całkowita 32-bitowa.|  
|`NATIVE_TYPE_U4`|Wartość liczby całkowitej bez znaku 32-bitowych.|  
|`NATIVE_TYPE_I8`|Wartość całkowita 64-bitowa.|  
|`NATIVE_TYPE_U8`|Wartość liczby całkowitej bez znaku 64-bitowych.|  
|`NATIVE_TYPE_R4`|4-bajtowych liczb zmiennoprzecinkowych wartość liczbową.|  
|`NATIVE_TYPE_R8`|8-bajtowych liczb zmiennoprzecinkowych wartość liczbowa.|  
|`NATIVE_TYPE_SYSCHAR`|Nieaktualne.|  
|`NATIVE_TYPE_VARIANT`|Nieaktualne.|  
|`NATIVE_TYPE_CURRENCY`|Typ liczbowy COM, umożliwiająca zarządzanej <xref:System.Decimal> typu.|  
|`NATIVE_TYPE_PTR`|Nieaktualne.|  
|`NATIVE_TYPE_DECIMAL`|Nieaktualne.|  
|`NATIVE_TYPE_DATE`|Nieaktualne.|  
|`NATIVE_TYPE_BSTR`|COM Interop.|  
|`NATIVE_TYPE_LPSTR`|Wartość ciągu LPSTR.|  
|`NATIVE_TYPE_LPWSTR`|Wartość ciągu LPWSTR.|  
|`NATIVE_TYPE_LPTSTR`|Wartość ciągu LPTSTR.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Wartość ciągu o stałej, zdefiniowane przez system.|  
|`NATIVE_TYPE_OBJECTREF`|Nieaktualne.|  
|`NATIVE_TYPE_IUNKNOWN`|COM Interop.|  
|`NATIVE_TYPE_IDISPATCH`|COM Interop.|  
|`NATIVE_TYPE_STRUCT`|Wartość native struktury.|  
|`NATIVE_TYPE_INTF`|COM Interop.|  
|`NATIVE_TYPE_SAFEARRAY`|COM Interop.|  
|`NATIVE_TYPE_FIXEDARRAY`|Wartość stałej długości tablicy.|  
|`NATIVE_TYPE_INT`|Wartość native 16-bitową liczbę całkowitą ze znakiem.|  
|`NATIVE_TYPE_UINT`|Wartość native liczbę całkowitą bez znaku 16-bitowych.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Nieaktualne.<br /><br /> Użyj NATIVE_TYPE_STRUCT.|  
|`NATIVE_TYPE_BYVALSTR`|COM Interop.|  
|`NATIVE_TYPE_ANSIBSTR`|COM Interop.|  
|`NATIVE_TYPE_TBSTR`|COM Interop.<br /><br /> Wybierz, BSTR lub ANSIBSTR w zależności od platformy.|  
|`NATIVE_TYPE_VARIANTBOOL`|2-bajtowych wartość logiczna, której prawdziwe wynosi -1 i FAŁSZ wynosi zero.|  
|`NATIVE_TYPE_FUNC`|Wskaźnik funkcji.|  
|`NATIVE_TYPE_ASANY`|Odwołanie do dowolnego typu macierzystego.|  
|`NATIVE_TYPE_ARRAY`|Odwołanie do tablicy z elementami członkowskimi nieokreślonego typu.|  
|`NATIVE_TYPE_LPSTRUCT`|32-bitową liczbę całkowitą wskaźnik do struktury.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Organizator niestandardowy typ macierzysty.<br /><br /> To musi następować ciąg o następującym formacie: "organizator nazwa/0Custom typ macierzysty typ nazwy/0Optional pliku cookie/0" lub "{natywnego typu GUID} / organizatora 0Custom wpisz nazwę/0Optional pliku cookie/0"|  
|`NATIVE_TYPE_ERROR`|COM Interop.<br /><br /> Z ELEMENT_TYPE_I4 VT_HRESULT mapuje tego typu.|  
|`NATIVE_TYPE_IINSPECTABLE`|Natywny `IInspectable` typu.|  
|`NATIVE_TYPE_HSTRING`|Natywny `HString`.|  
|`NATIVE_TYPE_MAX`|Określono nieprawidłową wartość.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.UnmanagedType>  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
