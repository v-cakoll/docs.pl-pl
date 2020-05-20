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
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="19de6-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition — Metoda</span><span class="sxs-lookup"><span data-stu-id="19de6-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>
<span data-ttu-id="19de6-103">Zwraca tablicę metod, z których każdy zawiera punkt przerwania w podanym miejscu w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="19de6-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19de6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19de6-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="19de6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19de6-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="19de6-106">podczas Określony dokument.</span><span class="sxs-lookup"><span data-stu-id="19de6-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="19de6-107">podczas Wiersz określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="19de6-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="19de6-108">podczas Kolumna określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="19de6-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="19de6-109">podczas Rozmiar `pRetVal` tablicy.</span><span class="sxs-lookup"><span data-stu-id="19de6-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="19de6-110">określoną Wskaźnik do zmiennej, która otrzymuje liczbę elementów zwracanych w `pRetVal` tablicy.</span><span class="sxs-lookup"><span data-stu-id="19de6-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="19de6-111">określoną Tablica wskaźników, z których każdy wskazuje obiekt [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) , który reprezentuje metodę zawierającą punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="19de6-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19de6-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="19de6-112">Return Value</span></span>  
 <span data-ttu-id="19de6-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="19de6-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19de6-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19de6-114">Requirements</span></span>  
 <span data-ttu-id="19de6-115">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="19de6-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19de6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19de6-116">See also</span></span>

- [<span data-ttu-id="19de6-117">ISymUnmanagedReader — Interfejs</span><span class="sxs-lookup"><span data-stu-id="19de6-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
