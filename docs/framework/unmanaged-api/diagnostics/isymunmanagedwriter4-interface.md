---
title: "ISymUnmanagedWriter4 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5531b491da70cb78de1234e750c2e15390c10ce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4 — Interfejs
Isymunmanagedwriter4 — interfejs.  
  
## <a name="syntax"></a>Składnia  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>Metody  
 Ten interfejs zawiera następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDebugInfoWithPadding, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|Działa tak samo, jak [GetDebugInfo — metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) z tą różnicą, że ciąg ścieżki jest uzupełniana zerami po znak końcowy null, aby udostępnić dane ciąg stały rozmiar `MAX_PATH`. Dopełnienie tylko otrzyma, jeśli długość ciągu ścieżki sam jest mniejsza niż `MAX_PATH`.<br /><br /> Ułatwia to zapisać narzędzia pliki tej różnicy PE.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedWriter3, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
