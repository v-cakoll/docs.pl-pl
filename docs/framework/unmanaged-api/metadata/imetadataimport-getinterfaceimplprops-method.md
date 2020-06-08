---
title: IMetaDataImport::GetInterfaceImplProps — Metoda
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: 1c9d9647084aa729817eeeb17ee3f5cd320c0d29
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491251"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps — Metoda
Pobiera wskaźnik do tokenów metadanych <xref:System.Type> , który implementuje określoną metodę i dla interfejsu, który deklaruje tę metodę.
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iiImpl`  
 podczas Token metadanych reprezentujący metodę zwracającą tokeny klasy i interfejsu dla.  
  
 `pClass`  
 określoną Token metadanych reprezentujący klasę implementującą metodę.  
  
 `ptkIface`  
 określoną Token metadanych reprezentujący interfejs, który definiuje zaimplementowaną metodę.  

## <a name="remarks"></a>Uwagi

 Uzyskujesz wartość dla `iImpl` przez wywołanie metody [EnumInterfaceImpls —](imetadataimport-enuminterfaceimpls-method.md) .

 Załóżmy na przykład, że Klasa ma `mdTypeDef` wartość tokenu 0x02000007 i implementuje trzy interfejsy, których typy mają tokeny:

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

Koncepcyjnie te informacje są przechowywane w tabeli implementacji interfejsu jako:

| Numer wiersza | Token klasy | Token interfejsu |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

Odwołaj, token jest wartością 4-bajtową:

- Dolne 3 bajty mają numer wiersza lub identyfikator RID.
- Górny bajt zawiera typ tokenu — 0x09 dla `mdtInterfaceImpl` .

`GetInterfaceImplProps`zwraca informacje przechowywane w wierszu, którego token jest udostępniany w `iImpl` argumencie.
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
