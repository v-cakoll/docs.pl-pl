---
title: ISymUnmanagedMethod::GetOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
ms.openlocfilehash: 358f3d3d7c231a2baa9d2c467935ba3a5867e36b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614477"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="71754-102">ISymUnmanagedMethod::GetOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="71754-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="71754-103">Zwraca przesunięcie w ramach tej metody, które odnosi się do danej pozycji w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="71754-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71754-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71754-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71754-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71754-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="71754-106">podczas Wskaźnik do dokumentu, dla którego zażądano przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="71754-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="71754-107">podczas Wiersz dokumentu, dla którego zażądano przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="71754-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="71754-108">podczas Kolumna dokumentu, dla której zażądano przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="71754-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="71754-109">określoną Wskaźnik do elementu `ULONG32` , który odbiera przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="71754-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71754-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="71754-110">Return Value</span></span>  
 <span data-ttu-id="71754-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="71754-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71754-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71754-112">Requirements</span></span>  
 <span data-ttu-id="71754-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="71754-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71754-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71754-114">See also</span></span>

- [<span data-ttu-id="71754-115">ISymUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="71754-115">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
