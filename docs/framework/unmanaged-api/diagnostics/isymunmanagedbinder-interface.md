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
ms.openlocfilehash: b6d91f68ac737ce28cdbef926119bb3711bc1096
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105822"
---
# <a name="isymunmanagedbinder-interface"></a>ISymUnmanagedBinder — Interfejs
Reprezentuje integrator symboli dla niezarządzanego kodu.  
  
> [!IMPORTANT]
>  Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych (PDB) programu z niezaufanego źródła.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReaderForFile, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|Podany interfejs metadanych i nazwę pliku, zwraca poprawny [isymunmanagedreader —](isymunmanagedreader-interface.md) strukturę, która będzie odczytywać symbole debugowania, skojarzone z modułem.|  
|[GetReaderFromStream, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|Podany interfejs metadanych i strumienia, który zawiera magazyn symboli, zwraca poprawny [isymunmanagedreader —](isymunmanagedreader-interface.md) strukturę, która będzie odczytywać debugowanie symboli z magazynu podanego symbolu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [ISymUnmanagedBinder3, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
