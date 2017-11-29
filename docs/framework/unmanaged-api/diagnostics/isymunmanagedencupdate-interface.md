---
title: "ISymUnmanagedENCUpdate — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate
helpviewer_keywords: ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 36ac53094751cb43ef122d439c7a784070c28182
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdate-interface"></a>ISymUnmanagedENCUpdate — Interfejs
Udostępnia funkcje dla funkcji Edytuj i Kontynuuj.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetLocalVariableCount — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|Pobiera liczbę zmiennych lokalnych.|  
|[GetLocalVariables — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|Pobiera zmienne lokalne.|  
|[InitializeForEnc — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|Umożliwia granice metody ma zostać obliczony przed pierwszym wywołaniu [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) metody.|  
|[UpdateMethodLines — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|Zezwala na aktualizowanie informacji linii dla metody, która nie zwrócenie, ale których wiersze zostały przeniesione osobno. Delta dla każdej instrukcji jest dozwolona.|  
|[UpdateSymbolStore2 — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|Umożliwia kompilatora pominąć funkcje, które nie zostały zmodyfikowane ze strumienia programu (PDB) bazy danych, pod warunkiem, że informacje dotyczące wiersza spełnia wymagania. Starych informacji PDB w wierszu i jeden delta dla wszystkich wierszy w funkcji można określić informacje dotyczące poprawne wiersza.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
