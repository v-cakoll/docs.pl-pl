---
title: ISymUnmanagedSymbolSearchInfo — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
ms.openlocfilehash: 308c501e17446719067d2dc0580d698c1770bf53
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610668"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a>ISymUnmanagedSymbolSearchInfo — Interfejs
Dostarcza metody, które pobierają informacje o ścieżce wyszukiwania. Uzyskaj ten interfejs, wywołując `QueryInterface` obiekt, który implementuje interfejs [ISymUnmanagedReader](isymunmanagedreader-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetHRESULT, metoda](isymunmanagedsymbolsearchinfo-gethresult-method.md)|Pobiera wartość HRESULT.|  
|[GetSearchPath, metoda](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|Pobiera ścieżkę wyszukiwania.|  
|[GetSearchPathLength, metoda](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|Pobiera długość ścieżki wyszukiwania.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](diagnostics-symbol-store-interfaces.md)
