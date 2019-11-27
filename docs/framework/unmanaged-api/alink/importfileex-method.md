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
ms.openlocfilehash: bee7db61beb9ed8c00cf584924be690a67d92eac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446952"
---
# <a name="importfileex-method"></a>ImportFileEx — Metoda
Importuje wskazany zestaw lub niezwiązany moduł.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `pszFilename`  
 W pełni kwalifikowana nazwa pliku, z którego ma zostać zaimportowana.  
  
 `pszTargetName`  
 Opcjonalna nazwa pliku docelowego.  
  
 `fSmartImport`  
 Jeśli wartość jest równa TRUE, używane są wartości, w przeciwnym razie importowanie należy wykonać ręcznie.  
  
 `dwOpenFlags`  
 Flagi do przesłania do [metody OpenScope —](../metadata/imetadatadispenser-openscope-method.md).  
  
 `pImportToken`  
 Odbiera identyfikator importowanego pliku.  
  
 `ppAssemblyScope`  
 Odbiera Interfejs [IMetaDataAssemblyImporty](../metadata/imetadataassemblyimport-interface.md) zakresu importu zestawu. Jest ustawiona na wartość NULL, jeśli plik nie jest zestawem.  
  
 `pdwCountOfScopes`  
 Odbiera liczbę zaimportowanych plików i/lub zakresów.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Zwraca S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga Alink. h.  
  
## <a name="see-also"></a>Zobacz także

- [IALink2, interfejs](ialink2-interface.md)
- [IALink, interfejs](ialink-interface.md)
- [ALink, interfejs API](index.md)
