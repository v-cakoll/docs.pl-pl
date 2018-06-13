---
title: ImportFileEx — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fe73bef50a32c3ff03f2a2754f665cc95018a4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402997"
---
# <a name="importfileex-method"></a>ImportFileEx — Metoda
Importy wskazane zestawu lub modułu niepowiązanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszFilename`  
 Pełna nazwa pliku, z którego będą importowane.  
  
 `pszTargetName`  
 Opcjonalna nazwa pliku docelowego.  
  
 `fSmartImport`  
 Jeśli PRAWDA, ImportTypes jest używany, w przeciwnym razie importowanie musi zostać wykonana ręcznie.  
  
 `dwOpenFlags`  
 Flagi są przekazywane do [OpenScope — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).  
  
 `pImportToken`  
 Odbiera identyfikator importowanego pliku.  
  
 `ppAssemblyScope`  
 Odbiera zakresu importu zestawu [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu. Jest ustawiony na wartość NULL, jeśli plik nie jest zestawem.  
  
 `pdwCountOfScopes`  
 Odbiera liczba importowanych plików i/lub zakresów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h.  
  
## <a name="see-also"></a>Zobacz też  
 [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
