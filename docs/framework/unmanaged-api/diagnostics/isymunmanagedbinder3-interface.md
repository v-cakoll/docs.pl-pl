---
title: "ISymUnmanagedBinder3 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder3 Interface
helpviewer_keywords: ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: df5cd6d4015fad1baf98909ee9cc923cd9bce05e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder3-interface"></a>ISymUnmanagedBinder3 — Interfejs
Rozszerzenie interfejsu integratora symbolu. Uzyskanie przez wywołanie metody tego interfejsu `QueryInterface` na obiekt, który implementuje `ISymUnmanagedBinder` interfejsu.  
  
> [!IMPORTANT]
>  Jest to zagrożenie, aby otworzyć plik programu (PDB) bazy danych z niezaufanego źródła.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReaderFromCallback — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|Zezwala użytkownikowi na wdrożenie lub podać za pośrednictwem wywołania zwrotnego albo `IID_IDiaReadExeAtRVACallback` lub `IID_IDiaReadExeAtOffsetCallback` Aby uzyskać informacje o debugowaniu katalogu z pamięci|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedBinder — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [ISymUnmanagedBinder2 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
