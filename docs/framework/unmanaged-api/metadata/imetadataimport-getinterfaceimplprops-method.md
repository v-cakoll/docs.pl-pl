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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76e2ebbd47a5e36a722fce33ba67d7efb4db8675
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115937"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps — Metoda
Pobiera wskaźnik do tokenów metadanych dla <xref:System.Type> implementującej określonej metody, a dla interfejsu, który deklaruje tej metody.
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iiImpl`  
 [in] Token metadanych reprezentujący metodę do zwrócenia klas i interfejsu tokeny zabezpieczające.  
  
 `pClass`  
 [out] Klasa, która implementuje metody reprezentująca token metadanych.  
  
 `ptkIface`  
 [out] Interfejs, który definiuje zaimplementowano metody reprezentująca token metadanych.  

## <a name="remarks"></a>Uwagi

 Uzyskaj wartość `iImpl` przez wywołanie metody [enuminterfaceimpls —](imetadataimport-enuminterfaceimpls-method.md) metody.
 
 Na przykład załóżmy, że klasa ma `mdTypeDef` token wartość 0x02000007 i implementuje trzy interfejsy, których typy mają tokenów: 

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

Koncepcyjnym te informacje są przechowywane w tabeli implementacji interfejsu jako:

| Numer wiersza | Klasa tokenu | Token interfejsu |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5          | 02000007    | 02000003        |
| 6          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

Pamiętasz, że token jest 4-bajtowych wartości:

- Niższe 3 bajtów hold numerem wiersza lub identyfikatorów RID.
- Górny bajtów zawiera typ tokenu — 0x09 `mdtInterfaceImpl`.

`GetInterfaceImplProps` Zwraca informacje przechowywane w wierszu, którego token podane `iImpl` argumentu. 
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
