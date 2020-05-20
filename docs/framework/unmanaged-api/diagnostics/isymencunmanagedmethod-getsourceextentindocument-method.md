---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument — Metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
ms.openlocfilehash: 3ac8bb3a20ce82b734a572832a9cbb75fa2568c4
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441906"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="049bd-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument — Metoda</span><span class="sxs-lookup"><span data-stu-id="049bd-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="049bd-103">Pobiera najmniejszą linię początkową i największą linię końcową dla metody w określonym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="049bd-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="049bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="049bd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="049bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="049bd-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="049bd-106">podczas Wskaźnik do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="049bd-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="049bd-107">określoną Wskaźnik do elementu `ULONG32` , który odbiera linię początkową.</span><span class="sxs-lookup"><span data-stu-id="049bd-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="049bd-108">określoną Wskaźnik do elementu `ULONG32` , który odbiera linię końcową.</span><span class="sxs-lookup"><span data-stu-id="049bd-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="049bd-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="049bd-109">Return Value</span></span>  
 <span data-ttu-id="049bd-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="049bd-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="049bd-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="049bd-111">Requirements</span></span>  
 <span data-ttu-id="049bd-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="049bd-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="049bd-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="049bd-113">See also</span></span>

- [<span data-ttu-id="049bd-114">ISymENCUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="049bd-114">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
