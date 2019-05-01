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
ms.openlocfilehash: bf62000fd4ec5c8f3dea3fa7d560b3f9ead33fa7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045472"
---
# <a name="cornativetype-enumeration"></a>CorNativeType — Wyliczenie
Zawiera wartości, które opisują typy natywne niezarządzanych.  
  
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
|`NATIVE_TYPE_BOOLEAN`|Wartość logiczna 4-bajtowych, gdzie wartość PRAWDA jest różna od zera i FALSE wynosi zero.|  
|`NATIVE_TYPE_I1`|Wartość całkowita 8-bitowa.|  
|`NATIVE_TYPE_U1`|Liczba całkowita bez znaku 8-bitową wartość.|  
|`NATIVE_TYPE_I2`|Wartość liczby całkowitej ze znakiem 16-bitowych.|  
|`NATIVE_TYPE_U2`|Liczba całkowita bez znaku 16-bitową wartość.|  
|`NATIVE_TYPE_I4`|Wartość całkowita 32-bitowa.|  
|`NATIVE_TYPE_U4`|Liczba całkowita bez znaku 32-bitowa wartość.|  
|`NATIVE_TYPE_I8`|Wartość całkowita 64-bitowa.|  
|`NATIVE_TYPE_U8`|Nieoznaczoną 64-bitowych wartość całkowitą.|  
|`NATIVE_TYPE_R4`|Zmiennoprzecinkowa wartość liczbowa 4-bajtowe.|  
|`NATIVE_TYPE_R8`|8-bajtowych zmiennoprzecinkowa wartość liczbowa.|  
|`NATIVE_TYPE_SYSCHAR`|Nieaktualne.|  
|`NATIVE_TYPE_VARIANT`|Nieaktualne.|  
|`NATIVE_TYPE_CURRENCY`|Typ liczbowy COM, odpowiadający zarządzanej <xref:System.Decimal> typu.|  
|`NATIVE_TYPE_PTR`|Nieaktualne.|  
|`NATIVE_TYPE_DECIMAL`|Nieaktualne.|  
|`NATIVE_TYPE_DATE`|Nieaktualne.|  
|`NATIVE_TYPE_BSTR`|Usługa międzyoperacyjna modelu COM.|  
|`NATIVE_TYPE_LPSTR`|Wartość ciągu LPSTR.|  
|`NATIVE_TYPE_LPWSTR`|Wartość ciągu LPWSTR.|  
|`NATIVE_TYPE_LPTSTR`|Wartość ciągu LPTSTR.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Wartość ciągu stałych, zdefiniowaną przez system.|  
|`NATIVE_TYPE_OBJECTREF`|Nieaktualne.|  
|`NATIVE_TYPE_IUNKNOWN`|Usługa międzyoperacyjna modelu COM.|  
|`NATIVE_TYPE_IDISPATCH`|Usługa międzyoperacyjna modelu COM.|  
|`NATIVE_TYPE_STRUCT`|Wartość natywnej struktury.|  
|`NATIVE_TYPE_INTF`|Usługa międzyoperacyjna modelu COM.|  
|`NATIVE_TYPE_SAFEARRAY`|Usługa międzyoperacyjna modelu COM.|  
|`NATIVE_TYPE_FIXEDARRAY`|Wartość stałej długości tablicy.|  
|`NATIVE_TYPE_INT`|Wartość natywnych liczby całkowitej ze znakiem 16-bitowych.|  
|`NATIVE_TYPE_UINT`|Wartość natywnych 16-bitowej nieoznaczonej liczby całkowitej.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Nieaktualne.<br /><br /> Użyj NATIVE_TYPE_STRUCT.|  
|`NATIVE_TYPE_BYVALSTR`|Usługa międzyoperacyjna modelu COM.|  
|`NATIVE_TYPE_ANSIBSTR`|Usługa międzyoperacyjna modelu COM.|  
|`NATIVE_TYPE_TBSTR`|Usługa międzyoperacyjna modelu COM.<br /><br /> Wybierz BSTR lub ANSIBSTR, w zależności od platformy.|  
|`NATIVE_TYPE_VARIANTBOOL`|2-bajtowych wartość logiczna, gdzie wartość PRAWDA jest wartość -1, a FAŁSZ jest równa zero.|  
|`NATIVE_TYPE_FUNC`|Wskaźnik funkcji.|  
|`NATIVE_TYPE_ASANY`|Odwołanie do dowolnego typu natywnego.|  
|`NATIVE_TYPE_ARRAY`|Odwołanie do tablicy o liczbie elementów członkowskich nieokreślonego typu.|  
|`NATIVE_TYPE_LPSTRUCT`|Wskaźnik 32-bitową liczbę całkowitą do struktury.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Organizator niestandardowy typ macierzysty.<br /><br /> To musi następować ciąg w następującym formacie: "Typ natywny nazwy/0Custom organizatora type nazwa/0Optional pliku cookie/0" lub "{natywnych wpisz identyfikator GUID} / organizatora 0Custom wpisz nazwę/0Optional pliku cookie/0"|  
|`NATIVE_TYPE_ERROR`|Usługa międzyoperacyjna modelu COM.<br /><br /> Za pomocą ELEMENT_TYPE_I4 VT_HRESULT mapuje tego typu.|  
|`NATIVE_TYPE_IINSPECTABLE`|Natywny `IInspectable` typu.|  
|`NATIVE_TYPE_HSTRING`|Natywny `HString`.|  
|`NATIVE_TYPE_MAX`|Nieprawidłowa wartość.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
