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
ms.openlocfilehash: aab42e939651d75b1933962d72ba8bec1090f52d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753468"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="6041d-102">PreCloseAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="6041d-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="6041d-103">Zamykanie pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="6041d-103">Closes the assembly file.</span></span> <span data-ttu-id="6041d-104">Wywołaj tę metodę po zamknięciu wszystkich innych plików, ale przed zamknięciem pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="6041d-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="6041d-105">Nie wywołuj tej metody dla modułów niepowiązanej.</span><span class="sxs-lookup"><span data-stu-id="6041d-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6041d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6041d-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6041d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6041d-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6041d-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="6041d-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6041d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6041d-109">Return Value</span></span>  
 <span data-ttu-id="6041d-110">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6041d-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6041d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6041d-111">Requirements</span></span>  
 <span data-ttu-id="6041d-112">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="6041d-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6041d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6041d-113">See also</span></span>

- [<span data-ttu-id="6041d-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="6041d-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="6041d-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6041d-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="6041d-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="6041d-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
