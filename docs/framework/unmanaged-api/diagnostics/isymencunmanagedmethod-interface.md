---
title: ISymENCUnmanagedMethod — Interfejs
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
ms.openlocfilehash: 54c8c7f5c3ba6b4afd4ff352a8afb947a92e2d61
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441880"
---
# <a name="isymencunmanagedmethod-interface"></a>ISymENCUnmanagedMethod — Interfejs
Zawiera informacje dotyczące funkcji Edytuj i Kontynuuj.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDocumentsForMethod, metoda](isymencunmanagedmethod-getdocumentsformethod-method.md)|Pobiera dokumenty, w których ta metoda zawiera wiersze.|  
|[GetDocumentsForMethodCount, metoda](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|Pobiera liczbę dokumentów, w których ta metoda zawiera wiersze.|  
|[GetFileNameFromOffset, metoda](isymencunmanagedmethod-getfilenamefromoffset-method.md)|Pobiera nazwę pliku dla wiersza skojarzonego z przesunięcia.|  
|[GetLineFromOffset, metoda](isymencunmanagedmethod-getlinefromoffset-method.md)|Pobiera informacje o wierszu skojarzone z przesunięciem.|  
|[GetSourceExtentInDocument, metoda](isymencunmanagedmethod-getsourceextentindocument-method.md)|Pobiera najmniejszą linię początkową i największą linię końcową dla metody w określonym dokumencie.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](diagnostics-symbol-store-interfaces.md)
