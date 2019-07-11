---
title: CloseAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18e0b7b3547bb246588f6b255483d4c317e0df88
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742228"
---
# <a name="closeassembly-method"></a><span data-ttu-id="31eae-102">CloseAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="31eae-102">CloseAssembly Method</span></span>
<span data-ttu-id="31eae-103">Kończenie znajdujących się w operacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="31eae-103">Finalizes assembly operations.</span></span> <span data-ttu-id="31eae-104">Tę metodę należy wywołać przed rozpoczęciem nowego zestawu lub modułu niepowiązanej.</span><span class="sxs-lookup"><span data-stu-id="31eae-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31eae-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="31eae-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="31eae-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="31eae-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="31eae-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="31eae-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31eae-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="31eae-108">Return Value</span></span>  
 <span data-ttu-id="31eae-109">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="31eae-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31eae-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31eae-110">Requirements</span></span>  
 <span data-ttu-id="31eae-111">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="31eae-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31eae-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31eae-112">See also</span></span>

- [<span data-ttu-id="31eae-113">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="31eae-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="31eae-114">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="31eae-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="31eae-115">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="31eae-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
