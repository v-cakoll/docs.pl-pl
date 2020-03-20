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
ms.openlocfilehash: b535fdd5027a26cc4dd0eafec9883f0186773dd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175502"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls — Metoda
Wylicza wszystkie interfejsy zaimplementowane przez określony `TypeDef`plik .
  
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
 [w, na zewnątrz] Wskaźnik do wyliczacza.  
  
 `td`  
 [w] Token TypeDef, którego tokeny MethodDef reprezentujące implementacje interfejsu mają być wyliczone.  
  
 `rImpls`  
 [na zewnątrz] Tablica używana do przechowywania tokenów MethodDef.  
  
 `cMax`  
 [w] Maksymalna długość `rImpls` tablicy.  
  
 `pcImpls`  
 [na zewnątrz] Rzeczywista liczba tokenów `rImpls`zwróconych w .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls`zwrócono pomyślnie.|  
|`S_FALSE`|Nie ma żadnych tokenów MethodDef do wyliczenia. W takim `pcImpls` przypadku jest ustawiona na zero.|  

## <a name="remarks"></a>Uwagi

Wyliczenie zwraca kolekcję `mdInterfaceImpl` tokenów dla każdego interfejsu `TypeDef`zaimplementowanego przez określony . Tokeny interfejsu są zwracane w kolejności, `DefineTypeDef` w `SetTypeDefProps`interfejsy zostały określone (za pośrednictwem lub ). Właściwości zwróconych `mdInterfaceImpl` tokenów można wyszukiwać za pomocą [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataImport — Interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
