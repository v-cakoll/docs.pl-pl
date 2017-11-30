---
title: "ImportFile — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile
helpviewer_keywords: ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 46830699ba43c406da313653e1910e8f7a18a2ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="importfile-method"></a>ImportFile — Metoda
Importuje zestawów i modułów niepowiązanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszFilename`  
 Pełna nazwa pliku do zaimportowania.  
  
 `pszTargetName`  
 Nazwa pliku wyjściowego opcjonalne, który może służyć do zmiany nazwy pliku, ponieważ jest on połączony w zestawie.  
  
 `fSmartImport`  
 Jeśli PRAWDA, ImportTypes jest używany, w przeciwnym razie importowanie musi zostać wykonana ręcznie.  
  
 `pImportToken`  
 Wskaźnik do tokenu, w którym będzie przechowywany Unikatowy identyfikator pliku. Może to być plik zestawu lub pliku.  
  
 `ppAssemblyScope`  
 Odbiera Wskaźnik do [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md). Może mieć wartości NULL, jeśli plik nie jest zestawem.  
  
 `pdwCountOfScopes`  
 Wskaźnik do liczby plików i/lub zakresy, które zostały zaimportowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ialink — interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Ialink2 — interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
