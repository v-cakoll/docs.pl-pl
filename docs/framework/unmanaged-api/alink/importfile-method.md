---
title: ImportFile — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69e48c6c3179ced167fdc39ae4df859f161727ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753520"
---
# <a name="importfile-method"></a>ImportFile — Metoda
Importuje zestawów i modułów niepowiązanej.  
  
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
  
## <a name="parameters"></a>Parametry  
 `pszFilename`  
 W pełni kwalifikowana nazwa pliku do zaimportowania.  
  
 `pszTargetName`  
 Nazwa pliku wyjściowego opcjonalny, którego można zmienić nazwy pliku, ponieważ jest on połączony do zestawu.  
  
 `fSmartImport`  
 W przypadku opcji TRUE importtypes — jest używana, w przeciwnym razie importowanie muszą być wykonywane ręcznie.  
  
 `pImportToken`  
 Wskaźnik do tokenu, gdzie będą przechowywane Unikatowy identyfikator pliku. Plik może być zestawu lub pliku.  
  
 `ppAssemblyScope`  
 Otrzymuje wskaźnik do [imetadataassemblyimport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md). Może mieć wartości NULL, jeśli plik nie jest zestawem.  
  
 `pdwCountOfScopes`  
 Wskaźnik do liczby plików i/lub zakresy, które zostały zaimportowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
