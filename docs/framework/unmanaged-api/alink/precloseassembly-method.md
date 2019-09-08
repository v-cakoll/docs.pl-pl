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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4cf862ae3676b85a7fc3f09a4f5794e01284737
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787235"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="50f87-102">PreCloseAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="50f87-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="50f87-103">Zamyka plik zestawu.</span><span class="sxs-lookup"><span data-stu-id="50f87-103">Closes the assembly file.</span></span> <span data-ttu-id="50f87-104">Wywołaj tę metodę po zamknięciu wszystkich innych plików, ale przed zamknięciem pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="50f87-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="50f87-105">Nie wywołuj tej metody dla modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="50f87-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50f87-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="50f87-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="50f87-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="50f87-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="50f87-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="50f87-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50f87-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="50f87-109">Return Value</span></span>  
 <span data-ttu-id="50f87-110">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="50f87-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50f87-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50f87-111">Requirements</span></span>  
 <span data-ttu-id="50f87-112">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="50f87-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f87-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50f87-113">See also</span></span>

- [<span data-ttu-id="50f87-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="50f87-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="50f87-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="50f87-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="50f87-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="50f87-116">ALink API</span></span>](index.md)
