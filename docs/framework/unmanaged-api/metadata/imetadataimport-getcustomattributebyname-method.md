---
title: IMetaDataImport::GetCustomAttributeByName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
ms.openlocfilehash: bd7ba7ff10918e5953ea8ae89a60af3115af48a3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437687"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a>IMetaDataImport::GetCustomAttributeByName — Metoda
Pobiera atrybut niestandardowy, uwzględniając jego nazwę i właściciela.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tkObj`  
 podczas Token metadanych reprezentujący obiekt będący właścicielem atrybutu niestandardowego.  
  
 `szName`  
 podczas Nazwa atrybutu niestandardowego.  
  
 `ppData`  
 określoną Wskaźnik do tablicy danych, która jest wartością atrybutu niestandardowego.  
  
 `pcbData`  
 określoną Rozmiar w bajtach danych zwróconych w *`ppData`.  
  
## <a name="remarks"></a>Uwagi  
 Istnieje możliwość zdefiniowania wielu atrybutów niestandardowych dla tego samego właściciela; mogą nawet mieć taką samą nazwę. Jednak `GetCustomAttributeByName` zwraca tylko jedno wystąpienie. (`GetCustomAttributeByName` zwraca pierwsze wystąpienie, które napotka.) Aby znaleźć wszystkie wystąpienia atrybutu niestandardowego, wywołaj metodę [IMetaDataImport:: EnumCustomAttributes —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
