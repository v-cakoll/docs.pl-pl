---
title: "ISymUnmanagedBinder — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder
helpviewer_keywords: ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5061ce28c4a09f445267c99420bf1942d99076bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder-interface"></a>ISymUnmanagedBinder — Interfejs
Reprezentuje integrator symbol dla kodu niezarządzanego.  
  
> [!IMPORTANT]
>  Jest to zagrożenie, aby otworzyć plik programu (PDB) bazy danych z niezaufanego źródła.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReaderForFile — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|Podany interfejs metadanych i nazwę pliku, zwraca poprawny <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> Struktura, która będzie odczytywać symbole debugowania skojarzone z modułu.|  
|[GetReaderFromStream — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|Podany interfejs metadanych i strumienia, który zawiera magazyn symbol zwraca poprawny <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> Struktura, która będzie odczytywać debugowanie symboli z magazynu podanego symbolu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedBinder2 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [ISymUnmanagedBinder3 — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
