---
title: ISymUnmanagedWriter3::OpenMethod2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
ms.openlocfilehash: e88a844a7f79f14c717a5966b345588b3b3b9f81
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609420"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="bba5b-102">ISymUnmanagedWriter3::OpenMethod2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="bba5b-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="bba5b-103">Otwiera metodę i udostępnia jej rzeczywiste przesunięcie sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="bba5b-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bba5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bba5b-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bba5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bba5b-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="bba5b-106">podczas Token metadanych dla metody, która ma zostać otwarta.</span><span class="sxs-lookup"><span data-stu-id="bba5b-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="bba5b-107">podczas Przesunięcie sekcji na obrazie.</span><span class="sxs-lookup"><span data-stu-id="bba5b-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="bba5b-108">podczas Przesunięcie na obrazie.</span><span class="sxs-lookup"><span data-stu-id="bba5b-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bba5b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bba5b-109">Return Value</span></span>  
 <span data-ttu-id="bba5b-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="bba5b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bba5b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bba5b-111">Requirements</span></span>  
 <span data-ttu-id="bba5b-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bba5b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bba5b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bba5b-113">See also</span></span>

- [<span data-ttu-id="bba5b-114">ISymUnmanagedWriter3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bba5b-114">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="bba5b-115">OpenMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="bba5b-115">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
