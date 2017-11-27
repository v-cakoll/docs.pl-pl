---
title: "IMetaDataImport::GetCustomAttributeByName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetCustomAttributeByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b689c54b5e8d741d32bc941b4e78e6674f15e01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
