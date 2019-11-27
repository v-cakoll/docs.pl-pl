---
title: PreCloseAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
ms.openlocfilehash: fcfd3e79bbb52837a333b5ffacf5c13ae60f2490
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445614"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="eb7ca-102">PreCloseAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="eb7ca-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="eb7ca-103">Zamyka plik zestawu.</span><span class="sxs-lookup"><span data-stu-id="eb7ca-103">Closes the assembly file.</span></span> <span data-ttu-id="eb7ca-104">Wywołaj tę metodę po zamknięciu wszystkich innych plików, ale przed zamknięciem pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="eb7ca-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="eb7ca-105">Nie wywołuj tej metody dla modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="eb7ca-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb7ca-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb7ca-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb7ca-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb7ca-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="eb7ca-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="eb7ca-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb7ca-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="eb7ca-109">Return Value</span></span>  
 <span data-ttu-id="eb7ca-110">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="eb7ca-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb7ca-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb7ca-111">Requirements</span></span>  
 <span data-ttu-id="eb7ca-112">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="eb7ca-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb7ca-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb7ca-113">See also</span></span>

- [<span data-ttu-id="eb7ca-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb7ca-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="eb7ca-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb7ca-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="eb7ca-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="eb7ca-116">ALink API</span></span>](index.md)
