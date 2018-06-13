---
title: ISymUnmanagedVariable — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3db4fc691637c049e0374416cb92a2056555ad11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428703"
---
# <a name="isymunmanagedvariable-interface"></a>ISymUnmanagedVariable — Interfejs
Reprezentuje zmienną, np. parametr, lokalnej zmiennej lub pola.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAddressField1, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|Pobiera pierwsze pole adresu dla tej zmiennej. Znaczenia zależy od rodzaju adres.|  
|[GetAddressField2, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|Pobiera drugie pole adresu dla tej zmiennej. Znaczenia zależy od rodzaju adres.|  
|[GetAddressField3, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|Pobiera trzecie pole adresu dla tej zmiennej. Znaczenia zależy od rodzaju adres.|  
|[GetAddressKind, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|Pobiera rodzaj adresu tej zmiennej.|  
|[GetAttributes, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|Pobiera atrybut Flagi dla tej zmiennej.|  
|[GetEndOffset, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|Pobiera przesunięcia końcowego tej zmiennej w ramach jego elementu nadrzędnego.|  
|[GetName, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|Pobiera nazwę zmiennej.|  
|[GetSignature, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|Pobiera podpis tej zmiennej.|  
|[GetStartOffset, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|Pobiera Przesunięcie początku tej zmiennej w ramach jego elementu nadrzędnego.|  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
