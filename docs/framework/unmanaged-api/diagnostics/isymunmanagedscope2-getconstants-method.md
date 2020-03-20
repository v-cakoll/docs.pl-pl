---
title: ISymUnmanagedScope2::GetConstants — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: 45268929b6e9ad6ac6423aa0fa2b7b5022bc9179
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176620"
---
# <a name="isymunmanagedscope2getconstants-method"></a>ISymUnmanagedScope2::GetConstants — Metoda
Pobiera stałe lokalne zdefiniowane w tym zakresie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cConstants`  
 [w] Długość buforu, na `pcConstants` który wskazuje parametr.  
  
 `pcConstants`  
 [na zewnątrz] Wskaźnik do, `ULONG32` który odbiera rozmiar, w znakach, buforu wymagane do zawierają stałe.  
  
 `constants`  
 [na zewnątrz] Bufor, który przechowuje stałe.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda powiedzie się; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też

- [ISymUnmanagedScope2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
