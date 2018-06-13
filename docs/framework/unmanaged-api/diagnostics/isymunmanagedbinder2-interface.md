---
title: ISymUnmanagedBinder2 — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 29501eeb6085dbc235112d98e8099fcfa4565000
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427798"
---
# <a name="isymunmanagedbinder2-interface"></a>ISymUnmanagedBinder2 — Interfejs
Reprezentuje integrator symbol dla niezarządzanego kodu i rozszerza [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interfejsu.  
  
> [!IMPORTANT]
>  Jest to zagrożenie, aby otworzyć plik programu (PDB) bazy danych z niezaufanego źródła.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReaderForFile2, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|Podany interfejs metadanych i nazwę pliku, zwraca poprawny <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interfejs, który będzie odczytywać symbole debugowania skojarzone z modułu. Zapewnia bardziej zaawansowane wyszukiwanie niż [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metody.|  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedBinder, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [ISymUnmanagedBinder3, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
