---
title: ISymUnmanagedBinder3 — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdfd8e8fc419809a3a490639ada1c533f286fe8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157511"
---
# <a name="isymunmanagedbinder3-interface"></a>ISymUnmanagedBinder3 — Interfejs
Rozszerza interfejs integratora symboli. Uzyskanie tego interfejsu, wywołując `QueryInterface` na obiekt, który implementuje `ISymUnmanagedBinder` interfejsu.  
  
> [!IMPORTANT]
>  Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych (PDB) programu z niezaufanego źródła.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReaderFromCallback, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|Zezwala użytkownikowi na implementowanie lub podać za pośrednictwem wywołania zwrotnego albo `IID_IDiaReadExeAtRVACallback` lub `IID_IDiaReadExeAtOffsetCallback` Aby uzyskać informacje o debugowaniu katalogu z pamięci|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder2 — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
