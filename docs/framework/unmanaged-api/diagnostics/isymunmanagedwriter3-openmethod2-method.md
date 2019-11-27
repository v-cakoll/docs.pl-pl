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
ms.openlocfilehash: 3a628aec0823c5db07d31d33813a020606906163
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438126"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="e9ddf-102">ISymUnmanagedWriter3::OpenMethod2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="e9ddf-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="e9ddf-103">Otwiera metodę i udostępnia jej rzeczywiste przesunięcie sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="e9ddf-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9ddf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9ddf-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9ddf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9ddf-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="e9ddf-106">podczas Token metadanych dla metody, która ma zostać otwarta.</span><span class="sxs-lookup"><span data-stu-id="e9ddf-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="e9ddf-107">podczas Przesunięcie sekcji na obrazie.</span><span class="sxs-lookup"><span data-stu-id="e9ddf-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="e9ddf-108">podczas Przesunięcie na obrazie.</span><span class="sxs-lookup"><span data-stu-id="e9ddf-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9ddf-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e9ddf-109">Return Value</span></span>  
 <span data-ttu-id="e9ddf-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e9ddf-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9ddf-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9ddf-111">Requirements</span></span>  
 <span data-ttu-id="e9ddf-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e9ddf-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9ddf-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9ddf-113">See also</span></span>

- [<span data-ttu-id="e9ddf-114">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="e9ddf-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="e9ddf-115">OpenMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="e9ddf-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
