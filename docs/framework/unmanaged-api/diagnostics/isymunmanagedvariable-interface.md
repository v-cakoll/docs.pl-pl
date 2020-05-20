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
ms.openlocfilehash: d05d4451e8fb75829b22e0a1b9c9afcb0607eb8b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610174"
---
# <a name="isymunmanagedvariable-interface"></a>ISymUnmanagedVariable — Interfejs
Reprezentuje zmienną, taką jak parametr, zmienna lokalna lub pole.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAddressField1, metoda](isymunmanagedvariable-getaddressfield1-method.md)|Pobiera pierwsze pole adresu dla tej zmiennej. Jego znaczenie zależy od rodzaju adresu.|  
|[GetAddressField2, metoda](isymunmanagedvariable-getaddressfield2-method.md)|Pobiera drugie pole adresu dla tej zmiennej. Jego znaczenie zależy od rodzaju adresu.|  
|[GetAddressField3, metoda](isymunmanagedvariable-getaddressfield3-method.md)|Pobiera trzecie pole adresu dla tej zmiennej. Jego znaczenie zależy od rodzaju adresu.|  
|[GetAddressKind, metoda](isymunmanagedvariable-getaddresskind-method.md)|Pobiera rodzaj adresu tej zmiennej.|  
|[GetAttributes, metoda](isymunmanagedvariable-getattributes-method.md)|Pobiera flagi atrybutu dla tej zmiennej.|  
|[GetEndOffset, metoda](isymunmanagedvariable-getendoffset-method.md)|Pobiera przesunięcie końca tej zmiennej w elemencie nadrzędnym.|  
|[GetName — Metoda](isymunmanagedvariable-getname-method.md)|Pobiera nazwę tej zmiennej.|  
|[GetSignature, metoda](isymunmanagedvariable-getsignature-method.md)|Pobiera sygnaturę tej zmiennej.|  
|[GetStartOffset, metoda](isymunmanagedvariable-getstartoffset-method.md)|Pobiera przesunięcie początku tej zmiennej w elemencie nadrzędnym.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy magazynu symboli diagnostycznych](diagnostics-symbol-store-interfaces.md)
