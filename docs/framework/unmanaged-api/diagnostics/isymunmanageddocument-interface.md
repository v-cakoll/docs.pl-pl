---
title: ISymUnmanagedDocument — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
ms.openlocfilehash: 3fa7b6b19d81e374cdb09b07ec181a7f4249a5eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449096"
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument — Interfejs
Reprezentuje dokument, do którego odwołuje się magazyn symboli. Dokument jest zdefiniowany przez adres URL (Uniform Resource Locator) i identyfikator GUID typu dokumentu. Możesz zlokalizować dokument niezależnie od tego, w jaki sposób jest przechowywany przy użyciu adresu URL i identyfikatora GUID typu dokumentu. Źródło dokumentu można zapisać w magazynie symboli i pobrać je za pomocą tego interfejsu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[FindClosestLine, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|Zwraca najbliższy wiersz będący punktem sekwencji, uwzględniając wiersz w tym dokumencie, który może lub nie jest punktem sekwencji.|  
|[GetCheckSum, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|Pobiera sumę kontrolną.|  
|[GetCheckSumAlgorithmId, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|Pobiera identyfikator algorytmu sum kontrolnych lub zwraca identyfikator GUID wszystkich zer, jeśli nie ma sumy kontrolnej.|  
|[GetDocumentType, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|Pobiera typ dokumentu tego dokumentu.|  
|[GetLanguage, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|Pobiera identyfikator języka tego dokumentu.|  
|[GetLanguageVendor, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|Pobiera dostawcę języka tego dokumentu.|  
|[GetSourceLength, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|Pobiera długość (w bajtach) osadzonego źródła.|  
|[GetSourceRange, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|Zwraca określony zakres osadzonego źródła do podanego buforu.|  
|[GetURL, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|Zwraca adres URL tego dokumentu.|  
|[HasEmbeddedSource, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|Zwraca `true`, jeśli dokument ma osadzone źródło w symbolach debugowania; w przeciwnym razie zwraca `false`.|  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
