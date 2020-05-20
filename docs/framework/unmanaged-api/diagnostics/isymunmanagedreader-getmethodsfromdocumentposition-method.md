---
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
ms.openlocfilehash: bba0fc039c403d45e8a5b60f2b0231eb24226280
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614958"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a>ISymUnmanagedReader::GetMethodsFromDocumentPosition — Metoda
Zwraca tablicę metod, z których każdy zawiera punkt przerwania w podanym miejscu w dokumencie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `document`  
 podczas Określony dokument.  
  
 `line`  
 podczas Wiersz określonego dokumentu.  
  
 `column`  
 podczas Kolumna określonego dokumentu.  
  
 `cMethod`  
 podczas Rozmiar `pRetVal` tablicy.  
  
 `pcMethod`  
 określoną Wskaźnik do zmiennej, która otrzymuje liczbę elementów zwracanych w `pRetVal` tablicy.  
  
 `pRetVal`  
 określoną Tablica wskaźników, z których każdy wskazuje obiekt [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) , który reprezentuje metodę zawierającą punkt przerwania.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedReader — Interfejs](isymunmanagedreader-interface.md)
