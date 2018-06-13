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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c25304bef4d240eedea749bb2829595056f9b74d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449250"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a>IMetaDataImport::GetCustomAttributeByName — Metoda
Pobiera atrybut niestandardowy podanej nazwy i właściciela.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tkObj`  
 [in] Token metadanych reprezentujący obiekt, który jest właścicielem atrybutu niestandardowego.  
  
 `szName`  
 [in] Nazwa atrybutu niestandardowego.  
  
 `ppData`  
 [out] Wskaźnik do tablicy danych, która jest wartością atrybutu niestandardowego.  
  
 `pcbData`  
 [out] Rozmiar w bajtach dane zwrócone w *`ppData`.  
  
## <a name="remarks"></a>Uwagi  
 Dozwolone jest zdefiniować wiele niestandardowych atrybutów tego samego właściciela; nawet mogą mieć takiej samej nazwie. Jednak `GetCustomAttributeByName` zwraca tylko jedno wystąpienie. (`GetCustomAttributeByName` zwraca pierwsze wystąpienie, które napotyka.) Aby znaleźć wszystkie wystąpienia atrybutu niestandardowego, należy wywołać [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
