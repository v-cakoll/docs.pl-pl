---
title: ISymUnmanagedMethod::GetRanges — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94ca1db2bf85f42117f686a8cb483907003927c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205852"
---
# <a name="isymunmanagedmethodgetranges-method"></a>ISymUnmanagedMethod::GetRanges — Metoda
Danou pozici w dokumencie zwraca tablicę rozpoczęcia i zakończenia pary przesunięcia, które odnoszą się do zakresów języka Microsoft intermediate language (MSIL) uwzględniającą pozycja w ramach tej metody. Tablica jest tablicy liczb całkowitych i ma format [rozpoczęcia, zakończenia, uruchamianie i kończenie]. Liczba par zakres jest długość tablicy podzielonej przez 2.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `document`  
 [in] Dokument, dla którego żądana jest przesunięcie.  
  
 `line`  
 [in] Wiersz dokumentu odpowiadający zakresów.  
  
 `column`  
 [in] Kolumna dokumentu, odpowiadający zakresów.  
  
 `cRanges`  
 [in] Rozmiar `ranges` tablicy.  
  
 `pcRanges`  
 [out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać zakresy.  
  
 `ranges`  
 [out] Wskaźnik do buforu, który otrzymuje zakresów.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedMethod — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
