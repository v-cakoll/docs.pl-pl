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
ms.openlocfilehash: 890053e1bf2e0648a41cca718e94edcf21c7e612
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165987"
---
# <a name="isymunmanagedreader2-interface"></a>ISymUnmanagedReader2 — Interfejs
Reprezentuje czytnik symbolu, który zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli. Ten interfejs rozszerza [isymunmanagedreader —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interfejsu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetMethodByVersionPreRemap, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|Uzyskaj metodę czytnika symboli podany token metody i numeru wersji edit-and-continue.|  
|[GetMethodsInDocument, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|Pobiera każdej metody, która ma informacje wiersza w podany dokument.|  
|[GetSymAttributePreRemap, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|Pobiera atrybut niestandardowy na podstawie jego nazwy.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
