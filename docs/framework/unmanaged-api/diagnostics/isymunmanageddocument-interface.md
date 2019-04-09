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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33213aced635549dd439cf679d89367a71baa7c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168808"
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument — Interfejs
Reprezentuje dokument odwołuje się w magazynie symboli. Dokument jest definiowany przez adres URL (adres URL) i identyfikator GUID typu dokumentu. Można zlokalizować dokument, niezależnie od tego, w jaki sposób są przechowywane przy użyciu adresu URL i identyfikator GUID typu dokumentu. Można przechowywać źródło dokumentu w magazynie symboli i pobrać go przy użyciu tego interfejsu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[FindClosestLine, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|Zwraca najbliższego wiersz, który jest punktem sekwencji, rozpoczynając od podanej linię w tym dokumencie, który może być lub może nie być punktu sekwencji.|  
|[GetCheckSum, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|Pobiera sumy kontrolnej.|  
|[GetCheckSumAlgorithmId, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|Pobiera identyfikator algorytmu sumy kontrolnej lub zwraca identyfikator GUID same zera, jeśli nie określono żadnych sumy kontrolnej.|  
|[GetDocumentType, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|Pobiera typ dokumentu w tym dokumencie.|  
|[GetLanguage, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|Pobiera identyfikator języka w tym dokumencie.|  
|[GetLanguageVendor, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|Pobiera dostawcę język tego dokumentu.|  
|[GetSourceLength, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|Pobiera długość w bajtach osadzonego źródła.|  
|[GetSourceRange, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|Zwraca określony zakres osadzonego źródła do podanego buforu.|  
|[GetURL, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|Zwraca adres URL dla tego dokumentu.|  
|[HasEmbeddedSource, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|Zwraca `true` Jeśli dokument ma źródło osadzone w symbole debugowania; w przeciwnym razie zwraca `false`.|  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
