---
title: ImportFile2 — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a03fc24e5ef932d13c0d195f53c703cdd3ff45ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776941"
---
# <a name="importfile2-method"></a>ImportFile2 — Metoda
Importuje zestawy i niepowiązane moduły. Ta metoda jest taka sama jak [Metoda ImportFile —](importfile-method.md), ale działa nawet wtedy, gdy importowany plik nie istnieje na dysku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszFilename`  
 Nazwa pliku do zaimportowania.  
  
 `pszTargetName`  
 Opcjonalna nazwa pliku wyjściowego, która może zostać użyta do zmiany nazwy pliku, ponieważ jest on połączony z zestawem.  
  
 `pAssemblyScopeIn`  
 Opcjonalny zakres interfejsu [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .  
  
 `fSmartImport`  
 Jeśli wartość jest równa TRUE, używane są wartości, w przeciwnym razie importowanie należy wykonać ręcznie.  
  
 `pImportToken`  
 Odbiera identyfikator dla pliku lub zestawu.  
  
 `ppAssemblyScope`  
 Odbiera Interfejs [interfejsu IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) . Wartość NULL, jeśli plik nie jest zestawem.  
  
 `pdwCountOfScopes`  
 Odbiera znalezione pliki i/lub zakresy zaimportowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga Alink. h.  
  
## <a name="see-also"></a>Zobacz także

- [IALink, interfejs](ialink-interface.md)
- [IALink2, interfejs](ialink2-interface.md)
- [ALink, interfejs API](index.md)
