---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPath — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type:
- apiref
ms.openlocfilehash: d9431a533a32fd15931072cfbabd10bbc0e6d4ad
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610681"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="532f1-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath — Metoda</span><span class="sxs-lookup"><span data-stu-id="532f1-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="532f1-103">Pobiera ścieżkę wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="532f1-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="532f1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="532f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="532f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="532f1-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="532f1-106">określoną Wskaźnik do obiektu, `ULONG32` który odbiera rozmiar (w znakach) bufora wymaganego do przechowywania ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="532f1-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="532f1-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="532f1-107">Return Value</span></span>  
 <span data-ttu-id="532f1-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="532f1-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="532f1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="532f1-109">Requirements</span></span>  
 <span data-ttu-id="532f1-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="532f1-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="532f1-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="532f1-111">See also</span></span>

- [<span data-ttu-id="532f1-112">ISymUnmanagedSymbolSearchInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="532f1-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
