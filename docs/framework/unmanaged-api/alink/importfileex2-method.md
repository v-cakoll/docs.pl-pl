---
title: ImportFileEx2 — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6584d31674670bcd005161a846b74df71a27a5f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741646"
---
# <a name="importfileex2-method"></a>ImportFileEx2 — Metoda
Importuje zestawów i modułów niepowiązanej. Ta metoda przypomina [importfile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ale wtedy, gdy importowanego pliku nie istnieje na dysku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszFilename`  
 Nazwa pliku do zaimportowania.  
  
 `pszTargetName`  
 Opcjonalna nazwa pliku docelowego.  
  
 `pAssemblyScopeIn`  
 Zakres opcjonalny import [imetadataassemblyimport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu.  
  
 `fSmartImport`  
 W przypadku opcji TRUE importtypes — jest używana, w przeciwnym razie importowanie muszą być wykonywane ręcznie.  
  
 `dwOpenFlags`  
 Flagi, aby być przekazywane do [openscope — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).  
  
 `pImportToken`  
 Otrzymuje unikatowy identyfikator zestawu lub pliku.  
  
 `ppAssemblyScope`  
 Odbiera zakresu importu zestawu [imetadataassemblyimport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu. Może mieć wartości NULL, jeśli plik nie jest zestawem.  
  
 `pdwCountOfScopes`  
 Odbiera liczbę plików i/lub zakresów zaimportowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h.  
  
## <a name="see-also"></a>Zobacz także

- [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
