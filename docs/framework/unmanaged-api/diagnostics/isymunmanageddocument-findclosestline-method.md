---
title: ISymUnmanagedDocument::FindClosestLine — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96ad0e34bf638c378f37e317f790696c2ac7cb25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519700"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a>ISymUnmanagedDocument::FindClosestLine — Metoda
Zwraca najbliższego wiersz, który jest punktem sekwencji, rozpoczynając od podanej linię w tym dokumencie, który może być lub może nie być punktu sekwencji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `line`  
 [in] Wiersz w tym dokumencie.  
  
 `pRetVal`  
 [out] Wskaźnik do zmiennej, która odbiera wiersza.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie kod błędu.  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedDocument, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
