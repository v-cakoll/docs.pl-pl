---
title: ISymUnmanagedMethod — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c29656a4787c674886505a3be2508470460dfc10
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136529"
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod — Interfejs
Reprezentuje metodę w magazynie symboli. Ten interfejs zapewnia dostęp do tylko powiązane symbol atrybuty metody, zamiast atrybutów związane z typu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetNamespace, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|Pobiera obszar nazw, w którym ta metoda jest zdefiniowana.|  
|[GetOffset, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|Zwraca przesunięcie w ramach tej metody, która odnosi się do określonej pozycji w dokumencie.|  
|[GetParameters, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|Pobiera parametry dla tej metody.|  
|[GetRanges, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|Danou pozici w dokumencie zwraca tablicę rozpoczęcia i zakończenia pary przesunięcia, które odnoszą się do zakresów języka Microsoft intermediate language (MSIL) uwzględniającą pozycja w ramach tej metody.|  
|[GetRootScope, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|Pobiera zakres leksykalne głównego w ramach tej metody. Ten zakres obejmuje całą metodę.|  
|[GetScopeFromOffset, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|Pobiera najbardziej otaczającym zakresie leksykalnym w ramach tej metody, która otacza danego przesunięcia.|  
|[GetSequencePointCount, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|Pobiera liczbę punktów sekwencji w ramach tej metody.|  
|[GetSequencePoints, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|Pobiera wszystkie punkty sekwencji w ramach tej metody.|  
|[GetSourceStartEnd, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|Pobiera położenie dokumentu rozpoczęcia i zakończenia dla źródłowej, tej metody.|  
|[GetToken, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|Zwraca token metadanych dla tej metody.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
