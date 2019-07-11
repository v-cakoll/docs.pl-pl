---
title: IMetaDataImport::EnumInterfaceImpls — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d0f94949cdc82cdecd52f003f3400c43014fabf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780463"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls — Metoda
Wylicza wszystkie interfejsy implementowane przez określony `TypeDef`. 
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `phEnum`  
 [out w] Wskaźnik do modułu wyliczającego.  
  
 `td`  
 [in] Token TypeDef, w których tokeny MethodDef reprezentujący implementacje interfejsu są do wyliczenia.  
  
 `rImpls`  
 [out] Tablica do przechowywania tokenów MethodDef.  
  
 `cMax`  
 [in] Maksymalny rozmiar `rImpls` tablicy.  
  
 `pcImpls`  
 [out] Rzeczywista liczba zwracane w tokenach `rImpls`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls` pomyślnie zwrócił.|  
|`S_FALSE`|Nie ma żadnych tokeny MethodDef do wyliczenia. W takim przypadku `pcImpls` jest równa zero.|  

## <a name="remarks"></a>Uwagi

Wyliczanie zwraca kolekcję `mdInterfaceImpl` tokenów dla każdego interfejsu implementowany przez określony `TypeDef`. Tokeny interfejsu są zwracane w porządku, o których określono interfejsy (za pośrednictwem `DefineTypeDef` lub `SetTypeDefProps`). Właściwości zwracanego `mdInterfaceImpl` tokeny mogą być przeszukiwane przy użyciu [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
