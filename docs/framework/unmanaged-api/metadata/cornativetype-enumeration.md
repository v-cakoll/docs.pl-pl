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
ms.openlocfilehash: 09a351db65c7ed310d3eb68c71a5207ed6040dd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177969"
---
# <a name="cornativetype-enumeration"></a>CorNativeType — Wyliczenie
Zawiera wartości opisujące natywne typy niezarządzane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|Nieaktualne.|  
|`NATIVE_TYPE_VOID`|Nieaktualne.|  
|`NATIVE_TYPE_BOOLEAN`|4-bajtowa wartość logiczna, gdzie wartość TRUE jest niezerowa, a wartość FALSE wynosi zero.|  
|`NATIVE_TYPE_I1`|Podpisana 8-bitowa wartość całkowita.|  
|`NATIVE_TYPE_U1`|Niepodpisana 8-bitowa wartość całkowita.|  
|`NATIVE_TYPE_I2`|Podpisana 16-bitowa wartość całkowita.|  
|`NATIVE_TYPE_U2`|Niepodpisana 16-bitowa wartość całkowita.|  
|`NATIVE_TYPE_I4`|Podpisana 32-bitowa wartość całkowita.|  
|`NATIVE_TYPE_U4`|Niepodpisana 32-bitowa wartość całkowita.|  
|`NATIVE_TYPE_I8`|Podpisana 64-bitowa wartość całkowita.|  
|`NATIVE_TYPE_U8`|Niepodpisana 64-bitowa wartość całkowita.|  
|`NATIVE_TYPE_R4`|4-bajtowa zmiennoprzecinczna wartość liczbowa.|  
|`NATIVE_TYPE_R8`|8-bajtowa zmiennoprzecinczna wartość liczbowa.|  
|`NATIVE_TYPE_SYSCHAR`|Nieaktualne.|  
|`NATIVE_TYPE_VARIANT`|Nieaktualne.|  
|`NATIVE_TYPE_CURRENCY`|Numeryczny typ COM, który odpowiada <xref:System.Decimal> typowi zarządzanemu.|  
|`NATIVE_TYPE_PTR`|Nieaktualne.|  
|`NATIVE_TYPE_DECIMAL`|Nieaktualne.|  
|`NATIVE_TYPE_DATE`|Nieaktualne.|  
|`NATIVE_TYPE_BSTR`|COM Interop.|  
|`NATIVE_TYPE_LPSTR`|Wartość ciągu LPSTR.|  
|`NATIVE_TYPE_LPWSTR`|Wartość ciągu LPWSTR.|  
|`NATIVE_TYPE_LPTSTR`|Wartość ciągu LPTSTR.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Stała, zdefiniowana przez system wartość ciągu.|  
|`NATIVE_TYPE_OBJECTREF`|Nieaktualne.|  
|`NATIVE_TYPE_IUNKNOWN`|COM Interop.|  
|`NATIVE_TYPE_IDISPATCH`|COM Interop.|  
|`NATIVE_TYPE_STRUCT`|Wartość struktury macierzystej.|  
|`NATIVE_TYPE_INTF`|COM Interop.|  
|`NATIVE_TYPE_SAFEARRAY`|COM Interop.|  
|`NATIVE_TYPE_FIXEDARRAY`|Wartość tablicy o stałej długości.|  
|`NATIVE_TYPE_INT`|Natywna 16-bitowa podpisana wartość całkowita.|  
|`NATIVE_TYPE_UINT`|Natywna 16-bitowa niepodpisana wartość całkowita.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Nieaktualne.<br /><br /> Użyj NATIVE_TYPE_STRUCT.|  
|`NATIVE_TYPE_BYVALSTR`|COM Interop.|  
|`NATIVE_TYPE_ANSIBSTR`|COM Interop.|  
|`NATIVE_TYPE_TBSTR`|COM Interop.<br /><br /> Wybierz BSTR lub ANSIBSTR w zależności od platformy.|  
|`NATIVE_TYPE_VARIANTBOOL`|2-bajtowa wartość logiczna, gdzie wartość TRUE wynosi -1, a FALSE wynosi zero.|  
|`NATIVE_TYPE_FUNC`|Wskaźnik funkcji.|  
|`NATIVE_TYPE_ASANY`|Odwołanie do dowolnego typu macierzystego.|  
|`NATIVE_TYPE_ARRAY`|Odwołanie do tablicy z elementami członkowskich nieokreślonego typu.|  
|`NATIVE_TYPE_LPSTRUCT`|32-bitowy wskaźnik liczby całkowitej do struktury.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Niestandardowy typ macierzysty organizatora.<br /><br /> Po tym musi następować ciąg o następującym formacie: "Nazwa typu macierzystego/0Nazwa typu organizatora/0Optional cookie/0" lub "{Typ macierzysty GUID}/0Nazwa typu organizatora aplikacji/0Optional cookie/0"|  
|`NATIVE_TYPE_ERROR`|COM Interop.<br /><br /> Z ELEMENT_TYPE_I4 tego typu mapuje do VT_HRESULT.|  
|`NATIVE_TYPE_IINSPECTABLE`|Typ `IInspectable` macierzysty.|  
|`NATIVE_TYPE_HSTRING`|Rodzimy `HString`.|  
|`NATIVE_TYPE_MAX`|Nieprawidłowa wartość.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
