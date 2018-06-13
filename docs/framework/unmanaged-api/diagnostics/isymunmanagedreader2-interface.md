---
title: ISymUnmanagedReader2 — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1dfc67ecf1eeb9ea5a19c98a8c378e73021da6c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426831"
---
# <a name="isymunmanagedreader2-interface"></a>ISymUnmanagedReader2 — Interfejs
Reprezentuje czytnika symboli, która zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli. Ten interfejs stanowi rozszerzenie [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interfejsu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetMethodByVersionPreRemap, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|Pobierz metodę czytnika symboli podany token metody i numer wersji edit-and-continue.|  
|[GetMethodsInDocument, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|Pobiera co metodę, która zawiera informacje dotyczące wiersza udostępnionego dokumentu.|  
|[GetSymAttributePreRemap, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|Pobiera atrybut niestandardowy ustalane na podstawie jego nazwy.|  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedReader, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
