---
title: ISymUnmanagedENCUpdate — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 378322c28d59b2a6e7c09f2f2c4bf55bb019d01d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171843"
---
# <a name="isymunmanagedencupdate-interface"></a>ISymUnmanagedENCUpdate — Interfejs
Oferuje funkcje funkcji Edytuj i Kontynuuj.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetLocalVariableCount, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|Pobiera liczbę zmiennych lokalnych.|  
|[GetLocalVariables, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|Pobiera zmienne lokalne.|  
|[InitializeForEnc, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|Umożliwia granice metody ma zostać obliczony przed pierwszym wywołaniu [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) metody.|  
|[UpdateMethodLines, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|Zezwala na aktualizowanie informacji o wierszu dla metody, która nie zwrócenie, ale których wiersze zostały przeniesione niezależnie. Delta dla każdej instrukcji jest dozwolona.|  
|[UpdateSymbolStore2, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|Umożliwia kompilatorowi pominąć funkcje, które nie zostały zmodyfikowane ze strumienia bazy danych (PDB) programu, pod warunkiem, że informacje wiersza spełnia wymagania. Informacje wiersza poprawne można ustalić przy użyciu starych informacji PDB w wierszu i jeden różnicowej dla wszystkich wierszy w funkcji.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
