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
ms.openlocfilehash: 32036058924aaf79fa7282144ced75040bc1f825
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426024"
---
# <a name="isymunmanagedmethodgetranges-method"></a>ISymUnmanagedMethod::GetRanges — Metoda
Podanej pozycji w dokumencie zwraca tablicę początkową i końcową pary przesunięcia, które odpowiadają zakresom język pośredni firmy Microsoft (MSIL), który obejmuje pozycję w ramach tej metody. Tablica jest tablicą liczb całkowitych i ma format [rozpoczęcia, zakończenia, start, zakończenie]. Określona liczba par zakres jest długość tablicy podzielona przez 2.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `document`  
 [in] Dokument, dla którego wnioskuje się przesunięcie.  
  
 `line`  
 [in] Wiersz dokumentu odpowiadający zakresów.  
  
 `column`  
 [in] Kolumna dokumentu odpowiadający zakresów.  
  
 `cRanges`  
 [in] Rozmiar `ranges` tablicy.  
  
 `pcRanges`  
 [out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać zakresów.  
  
 `ranges`  
 [out] Wskaźnik do buforu, który odbiera zakresów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedMethod, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
