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
ms.openlocfilehash: 910c40413075131765a37e00703ac892e3f39641
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492229"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls — Metoda
Wylicza wszystkie interfejsy zaimplementowane przez określony `TypeDef` .
  
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
 [in. out] Wskaźnik do modułu wyliczającego.  
  
 `td`  
 podczas Token elementu TypeDef, którego tokeny MethodDef reprezentują implementacje interfejsów, mają zostać wyliczone.  
  
 `rImpls`  
 określoną Tablica służąca do przechowywania tokenów MethodDef.  
  
 `cMax`  
 podczas Maksymalna długość `rImpls` tablicy.  
  
 `pcImpls`  
 określoną Rzeczywista liczba tokenów zwrócona w `rImpls` .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls`pomyślnie zwrócono.|  
|`S_FALSE`|Brak tokenów MethodDef do wyliczenia. W takim przypadku `pcImpls` jest ustawiona na zero.|  

## <a name="remarks"></a>Uwagi

Wyliczenie zwraca kolekcję `mdInterfaceImpl` tokenów dla każdego interfejsu zaimplementowanego przez określony `TypeDef` . Tokeny interfejsu są zwracane w kolejności, w jakiej interfejsy zostały określone (za pomocą `DefineTypeDef` lub `SetTypeDefProps` ). Do właściwości zwracanych `mdInterfaceImpl` tokenów można wykonywać zapytania przy użyciu [GetInterfaceImplProps —](imetadataimport-getinterfaceimplprops-method.md).
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
