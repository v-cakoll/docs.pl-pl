---
title: ISymUnmanagedWriter::RemapToken — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
ms.openlocfilehash: 53cc908e0dc8cc5cc980ec365ccac0df4e620cac
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609771"
---
# <a name="isymunmanagedwriterremaptoken-method"></a>ISymUnmanagedWriter::RemapToken — Metoda
Powiadamia moduł zapisujący symboli o tym, że token metadanych został ponownie zmapowany w miarę emitowania metadanych. Jeśli moduł zapisujący symboli przechowuje stary token w magazynie symboli, musi zaktualizować przechowywany token nową wartością lub zapisać mapę dla odpowiedniego czytnika symboli do ponownego mapowania w fazie odczytu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a>Parametry  
 `oldToken`  
 podczas Token metadanych, który został ponownie zamapowany.  
  
 `newToken`  
 podczas Nowy token metadanych, który `oldToken` został ponownie zamapowany.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter — Interfejs](isymunmanagedwriter-interface.md)
