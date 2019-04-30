---
title: ISymUnmanagedScope2 — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0109b25b1cdc42204fc4873577e495641c4ec4fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761575"
---
# <a name="isymunmanagedscope2-interface"></a>ISymUnmanagedScope2 — Interfejs
Reprezentuje zakresie leksykalnym wewnątrz metody. Ten interfejs rozszerza [isymunmanagedscope —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interfejs, za pomocą metod, które uzyskać informacje na temat stałe zdefiniowane w zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetConstantCount, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|Pobiera liczbę stałe zdefiniowane w tym zakresie.|  
|[GetConstants, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|Pobiera lokalne stałe zdefiniowane w tym zakresie.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedScope, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
