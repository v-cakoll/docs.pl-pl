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
ms.openlocfilehash: 712eca7f3f9fec9c81e638802f5a664ec6469d53
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164349"
---
# <a name="isymunmanagedvariable-interface"></a>ISymUnmanagedVariable — Interfejs
Reprezentuje zmienną, takie jak parametr, zmienna lokalna lub pola.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAddressField1, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|Pobiera pierwsze pole Adres dla tej zmiennej. Znaczenia, zależy od rodzaju adresu.|  
|[GetAddressField2, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|Pobiera drugie pole Adres dla tej zmiennej. Znaczenia, zależy od rodzaju adresu.|  
|[GetAddressField3, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|Pobiera trzecim polu adresów dla tej zmiennej. Znaczenia, zależy od rodzaju adresu.|  
|[GetAddressKind, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|Pobiera rodzaj adres tej zmiennej.|  
|[GetAttributes, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|Pobiera flagi atrybutów dla tej zmiennej.|  
|[GetEndOffset, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|Pobiera końcowy przesunięcie tej zmiennej w ramach jego elementu nadrzędnego.|  
|[GetName, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|Pobiera nazwę tej zmiennej.|  
|[GetSignature, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|Pobiera podpis tej zmiennej.|  
|[GetStartOffset, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|Pobiera Przesunięcie początku tej zmiennej w ramach jego elementu nadrzędnego.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
