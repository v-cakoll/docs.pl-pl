---
title: "ISymUnmanagedENCUpdate::UpdateSymbolStore2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1c0ff6d48bc749b1d8850f94fb1dc1adf3de8e37
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a>ISymUnmanagedENCUpdate::UpdateSymbolStore2 — Metoda
Umożliwia kompilatora pominąć funkcje, które nie zostały zmodyfikowane ze strumienia programu (PDB) bazy danych, podane informacje dotyczące wiersza spełnia wymagania. Starych informacji PDB w wierszu i jeden delta dla wszystkich wierszy w funkcji można określić informacje dotyczące poprawne wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pIStream`  
 [in] Wskaźnik do <xref:IStream> zawierający informacje dotyczące wiersza.  
  
 `pDeltaLines`  
 [in] Wskaźnik do [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) strukturę, która zawiera wiersze, które zostały zmienione.  
  
 `cDeltaLines`  
 [in] A `ULONG` reprezentujący liczbę wierszy, które zostały zmienione.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedENCUpdate — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
