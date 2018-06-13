---
title: ISymUnmanagedBinder — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7bbdc4b1f15c8dbb154ed7b967bb21c61d11782a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425555"
---
# <a name="isymunmanagedbinder-interface"></a>ISymUnmanagedBinder — Interfejs
Reprezentuje integrator symbol dla kodu niezarządzanego.  
  
> [!IMPORTANT]
>  Jest to zagrożenie, aby otworzyć plik programu (PDB) bazy danych z niezaufanego źródła.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReaderForFile, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|Podany interfejs metadanych i nazwę pliku, zwraca poprawny [ISymUnmanagedReader](isymunmanagedreader-interface.md) strukturę, która będzie odczytywać symbole debugowania skojarzone z modułu.|  
|[GetReaderFromStream, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|Podany interfejs metadanych i strumienia, który zawiera magazyn symbol zwraca poprawny [ISymUnmanagedReader](isymunmanagedreader-interface.md) strukturę, która będzie odczytywać debugowanie symboli z magazynu podanego symbolu.|  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedBinder2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [ISymUnmanagedBinder3, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
