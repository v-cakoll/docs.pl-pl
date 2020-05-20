---
title: ISymUnmanagedWriter2 — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
ms.openlocfilehash: 1fe6055d930c6d30e947d6bc774d0520a9e175ae
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614685"
---
# <a name="isymunmanagedwriter2-interface"></a>ISymUnmanagedWriter2 — Interfejs
Reprezentuje moduł zapisujący symboli i zawiera metody definiowania dokumentów, punktów sekwencji, zakresów leksykalnych i zmiennych. Ten interfejs rozszerza interfejs [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[DefineConstant2, metoda](isymunmanagedwriter2-defineconstant2-method.md)|Definiuje nazwę wartości stałej.|  
|[DefineGlobalVariable2, metoda](isymunmanagedwriter2-defineglobalvariable2-method.md)|Definiuje pojedynczą zmienną globalną.|  
|[DefineLocalVariable2, metoda](isymunmanagedwriter2-definelocalvariable2-method.md)|Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter — Interfejs](isymunmanagedwriter-interface.md)
- [ISymUnmanagedWriter3 — Interfejs](isymunmanagedwriter3-interface.md)
