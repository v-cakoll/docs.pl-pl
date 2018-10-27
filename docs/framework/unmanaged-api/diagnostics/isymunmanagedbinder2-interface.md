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
ms.openlocfilehash: 52b0f6b9d3e0ea3d6fe5f14badb8401b1a0c2c63
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187495"
---
# <a name="isymunmanagedbinder2-interface"></a>ISymUnmanagedBinder2 — Interfejs
Reprezentuje integrator symboli dla niezarządzanego kodu i rozszerza [isymunmanagedbinder —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interfejsu.  
  
> [!IMPORTANT]
>  Jest to zagrożenie bezpieczeństwa, aby otworzyć plik bazy danych (PDB) programu z niezaufanego źródła.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReaderForFile2, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|Podany interfejs metadanych i nazwę pliku, zwraca poprawny [isymunmanagedreader —](isymunmanagedreader-interface.md) interfejs, który zostanie odczytany symbole debugowania, skojarzone z modułem. Zapewnia bardziej rozbudowane wyszukiwanie niż [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metody.|  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedBinder, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [ISymUnmanagedBinder3, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
