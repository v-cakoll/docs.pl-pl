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
ms.openlocfilehash: 4b8ddf7fec12d175f030c0ea0ed982c6fb334aee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175385"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps — Metoda
Pobiera wskaźnik do tokenów metadanych dla <xref:System.Type> tego implementuje określoną metodę i dla interfejsu, który deklaruje tę metodę.
  
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
 [w] Token metadanych reprezentujący metodę zwracania tokenów klasy i interfejsu.  
  
 `pClass`  
 [na zewnątrz] Token metadanych reprezentujący klasę, która implementuje metodę.  
  
 `ptkIface`  
 [na zewnątrz] Token metadanych reprezentujący interfejs, który definiuje zaimplementowana metoda.  

## <a name="remarks"></a>Uwagi

 Można uzyskać wartość `iImpl` dla wywołując [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) metody.

 Załóżmy na przykład, `mdTypeDef` że klasa ma wartość tokenu 0x02000007 i implementuje trzy interfejsy, których typy mają tokeny:

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

Przypomnijmy, token jest wartością 4-bajtową:

- Dolne 3 bajty przytrzymują numer wiersza lub RID.
- Górny bajt zawiera typ tokenu — `mdtInterfaceImpl`0x09 dla .

`GetInterfaceImplProps`zwraca informacje przechowywane w wierszu, którego `iImpl` token można podać w argumie.
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
