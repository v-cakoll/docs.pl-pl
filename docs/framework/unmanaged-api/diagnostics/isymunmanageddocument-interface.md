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
ms.openlocfilehash: a8ff6d3a925773e58e0713a87b167420c246f85b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615569"
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument — Interfejs
Reprezentuje dokument, do którego odwołuje się magazyn symboli. Dokument jest zdefiniowany przez adres URL (Uniform Resource Locator) i identyfikator GUID typu dokumentu. Możesz zlokalizować dokument niezależnie od tego, w jaki sposób jest przechowywany przy użyciu adresu URL i identyfikatora GUID typu dokumentu. Źródło dokumentu można zapisać w magazynie symboli i pobrać je za pomocą tego interfejsu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[FindClosestLine, metoda](isymunmanageddocument-findclosestline-method.md)|Zwraca najbliższy wiersz będący punktem sekwencji, uwzględniając wiersz w tym dokumencie, który może lub nie jest punktem sekwencji.|  
|[GetCheckSum, metoda](isymunmanageddocument-getchecksum-method.md)|Pobiera sumę kontrolną.|  
|[GetCheckSumAlgorithmId, metoda](isymunmanageddocument-getchecksumalgorithmid-method.md)|Pobiera identyfikator algorytmu sum kontrolnych lub zwraca identyfikator GUID wszystkich zer, jeśli nie ma sumy kontrolnej.|  
|[GetDocumentType, metoda](isymunmanageddocument-getdocumenttype-method.md)|Pobiera typ dokumentu tego dokumentu.|  
|[GetLanguage, metoda](isymunmanageddocument-getlanguage-method.md)|Pobiera identyfikator języka tego dokumentu.|  
|[GetLanguageVendor, metoda](isymunmanageddocument-getlanguagevendor-method.md)|Pobiera dostawcę języka tego dokumentu.|  
|[GetSourceLength, metoda](isymunmanageddocument-getsourcelength-method.md)|Pobiera długość (w bajtach) osadzonego źródła.|  
|[GetSourceRange, metoda](isymunmanageddocument-getsourcerange-method.md)|Zwraca określony zakres osadzonego źródła do podanego buforu.|  
|[GetURL, metoda](isymunmanageddocument-geturl-method.md)|Zwraca adres URL tego dokumentu.|  
|[HasEmbeddedSource, metoda](isymunmanageddocument-hasembeddedsource-method.md)|Zwraca `true` czy dokument ma osadzone źródło w symbolach debugowania; w przeciwnym razie zwraca `false` .|  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](diagnostics-symbol-store-interfaces.md)
