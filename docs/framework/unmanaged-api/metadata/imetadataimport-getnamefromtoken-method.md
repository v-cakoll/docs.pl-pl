---
title: IMetaDataImport::GetNameFromToken — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
ms.openlocfilehash: 6d62739148280c7333cf7cdb6002b59a145496e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503565"
---
# <a name="imetadataimportgetnamefromtoken-method"></a>IMetaDataImport::GetNameFromToken — Metoda
Pobiera nazwę UTF-8 obiektu, do którego odwołuje się określony token metadanych. Ta metoda jest przestarzała.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 podczas Token reprezentujący obiekt, dla którego ma zostać zwrócona nazwa.  
  
 `pszUtf8NamePtr`  
 określoną Wskaźnik do nazwy obiektu UTF-8 w stercie.  
  
## <a name="remarks"></a>Uwagi  
 `GetNameFromToken`jest przestarzały. Alternatywnie Wywołaj metodę, aby uzyskać właściwości określonego typu wymaganego tokenu, na przykład `GetFieldProps` dla pola lub `GetMethodProps` dla metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:** 1,0  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
