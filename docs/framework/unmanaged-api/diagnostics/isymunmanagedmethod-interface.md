---
title: "ISymUnmanagedMethod — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b6305625c3d02dbd126a284287e19b319e21eeba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod — Interfejs
Reprezentuje metodę w magazynie symboli. Ten interfejs umożliwia dostęp do tylko powiązane symbol atrybuty metody, zamiast atrybutów związanych z typu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetNamespace, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|Pobiera obszar nazw, w którym ta metoda jest zdefiniowana.|  
|[GetOffset, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|Zwraca przesunięcie w ramach tej metody, która odpowiada na określonej pozycji w dokumencie.|  
|[GetParameters, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|Pobiera parametry dla tej metody.|  
|[GetRanges, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|Podanej pozycji w dokumencie zwraca tablicę początkową i końcową pary przesunięcia, które odpowiadają zakresom język pośredni firmy Microsoft (MSIL), który obejmuje pozycję w ramach tej metody.|  
|[GetRootScope, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|Pobiera zakres leksykalne głównego w ramach tej metody. Ten zakres obejmuje całą metody.|  
|[GetScopeFromOffset, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|Pobiera najbardziej otaczającym zakresie leksykalne w ramach tej metody, które umieszcza danego przesunięcia.|  
|[GetSequencePointCount, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|Pobiera liczbę punktów sekwencji w ramach tej metody.|  
|[GetSequencePoints, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|Pobiera wszystkie punkty sekwencji w ramach tej metody.|  
|[GetSourceStartEnd, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|Pobiera dokument pozycje początkowe i końcowe dla źródła tej metody.|  
|[GetToken, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|Zwraca token metadanych dla tej metody.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
