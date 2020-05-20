---
title: ISymUnmanagedReader::GetMethodFromDocumentPosition — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type:
- apiref
ms.openlocfilehash: 8015056b110fe8a5b5122b1bc81143980b780047
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614984"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="62abd-102">ISymUnmanagedReader::GetMethodFromDocumentPosition — Metoda</span><span class="sxs-lookup"><span data-stu-id="62abd-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="62abd-103">Zwraca metodę, która zawiera punkt przerwania w podanym miejscu w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="62abd-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62abd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62abd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62abd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62abd-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="62abd-106">podczas Określony dokument.</span><span class="sxs-lookup"><span data-stu-id="62abd-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="62abd-107">podczas Wiersz określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="62abd-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="62abd-108">podczas Kolumna określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="62abd-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="62abd-109">określoną Wskaźnik do adresu obiektu [interfejsu ISymUnmanagedMethod](isymunmanagedmethod-interface.md) , który reprezentuje metodę zawierającą punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="62abd-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62abd-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="62abd-110">Return Value</span></span>  
 <span data-ttu-id="62abd-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="62abd-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62abd-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62abd-112">Requirements</span></span>  
 <span data-ttu-id="62abd-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="62abd-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62abd-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62abd-114">See also</span></span>

- [<span data-ttu-id="62abd-115">ISymUnmanagedReader — Interfejs</span><span class="sxs-lookup"><span data-stu-id="62abd-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
