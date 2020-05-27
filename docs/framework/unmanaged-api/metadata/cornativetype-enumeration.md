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
ms.openlocfilehash: dd97c479f12e7bdb015b39a802b398ca2b0bcd3f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007640"
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
|`NATIVE_TYPE_BOOLEAN`|4-bajtowa wartość logiczna, gdzie TRUE ma wartość różną od zera, a wartość FALSE to zero.|  
|`NATIVE_TYPE_I1`|8-bitowa liczba całkowita ze znakiem.|  
|`NATIVE_TYPE_U1`|8-bitowa liczba całkowita bez znaku.|  
|`NATIVE_TYPE_I2`|Wartość 16-bitowa ze znakiem.|  
|`NATIVE_TYPE_U2`|16-bitowa liczba całkowita bez znaku.|  
|`NATIVE_TYPE_I4`|Podpisana 32-bitowa liczba całkowita.|  
|`NATIVE_TYPE_U4`|Niepodpisana wartość 32-bitowa liczba całkowita.|  
|`NATIVE_TYPE_I8`|Podpisana 64-bitowa liczba całkowita.|  
|`NATIVE_TYPE_U8`|Niepodpisana wartość 64-bitowa liczba całkowita.|  
|`NATIVE_TYPE_R4`|4-bajtowa wartość liczbowa zmiennoprzecinkowa.|  
|`NATIVE_TYPE_R8`|8-bajtowa wartość liczbowa zmiennoprzecinkowa.|  
|`NATIVE_TYPE_SYSCHAR`|Nieaktualne.|  
|`NATIVE_TYPE_VARIANT`|Nieaktualne.|  
|`NATIVE_TYPE_CURRENCY`|Liczbowy typ COM, który odpowiada typowi zarządzanemu <xref:System.Decimal> .|  
|`NATIVE_TYPE_PTR`|Nieaktualne.|  
|`NATIVE_TYPE_DECIMAL`|Nieaktualne.|  
|`NATIVE_TYPE_DATE`|Nieaktualne.|  
|`NATIVE_TYPE_BSTR`|Międzyoperacyjność modelu COM.|  
|`NATIVE_TYPE_LPSTR`|Wartość ciągu LPSTR.|  
|`NATIVE_TYPE_LPWSTR`|Wartość ciągu LPWSTR.|  
|`NATIVE_TYPE_LPTSTR`|Wartość ciągu LPTSTR.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Stała, zdefiniowana przez system wartość ciągu.|  
|`NATIVE_TYPE_OBJECTREF`|Nieaktualne.|  
|`NATIVE_TYPE_IUNKNOWN`|Międzyoperacyjność modelu COM.|  
|`NATIVE_TYPE_IDISPATCH`|Międzyoperacyjność modelu COM.|  
|`NATIVE_TYPE_STRUCT`|Wartość struktury natywnej.|  
|`NATIVE_TYPE_INTF`|Międzyoperacyjność modelu COM.|  
|`NATIVE_TYPE_SAFEARRAY`|Międzyoperacyjność modelu COM.|  
|`NATIVE_TYPE_FIXEDARRAY`|Wartość tablicy o stałej długości.|  
|`NATIVE_TYPE_INT`|Natywna 16-bitowa liczba całkowita ze znakiem.|  
|`NATIVE_TYPE_UINT`|Natywna 16-bitowa liczba całkowita bez znaku.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Nieaktualne.<br /><br /> Użyj NATIVE_TYPE_STRUCT.|  
|`NATIVE_TYPE_BYVALSTR`|Międzyoperacyjność modelu COM.|  
|`NATIVE_TYPE_ANSIBSTR`|Międzyoperacyjność modelu COM.|  
|`NATIVE_TYPE_TBSTR`|Międzyoperacyjność modelu COM.<br /><br /> W zależności od platformy wybierz opcję BSTR lub ANSIBSTR.|  
|`NATIVE_TYPE_VARIANTBOOL`|Wartość 2-bajtowa wartości logicznej, gdzie TRUE to-1, a FALSE to zero.|  
|`NATIVE_TYPE_FUNC`|Wskaźnik funkcji.|  
|`NATIVE_TYPE_ASANY`|Odwołanie do dowolnego typu natywnego.|  
|`NATIVE_TYPE_ARRAY`|Odwołanie do tablicy z elementami członkowskimi nieokreślonego typu.|  
|`NATIVE_TYPE_LPSTRUCT`|32-bitowy wskaźnik liczby całkowitej do struktury.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Typ natywny organizatora niestandardowego.<br /><br /> Musi to być ciąg o następującym formacie: "native type name/0Custom typ marshaler/0Optional cookie/0" lub "{native Type GUID}/0Custom typu nazwa/0Optional cookie/0"|  
|`NATIVE_TYPE_ERROR`|Międzyoperacyjność modelu COM.<br /><br /> Dzięki ELEMENT_TYPE_I4 ten typ mapuje do VT_HRESULT.|  
|`NATIVE_TYPE_IINSPECTABLE`|Typ natywny `IInspectable` .|  
|`NATIVE_TYPE_HSTRING`|Natywny `HString` .|  
|`NATIVE_TYPE_MAX`|Nieprawidłowa wartość.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [Wyliczenia metadanych](metadata-enumerations.md)
