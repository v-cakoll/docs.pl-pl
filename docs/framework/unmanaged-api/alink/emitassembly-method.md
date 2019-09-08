---
title: EmitAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2adf53d1e29fda077cdcf7b79891f6271993109
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787580"
---
# <a name="emitassembly-method"></a><span data-ttu-id="34fca-102">EmitAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="34fca-102">EmitAssembly Method</span></span>
<span data-ttu-id="34fca-103">Tworzy zestaw.</span><span class="sxs-lookup"><span data-stu-id="34fca-103">Creates the assembly.</span></span> <span data-ttu-id="34fca-104">Wywołaj tę metodę po zamknięciu wszystkich innych plików z wyjątkiem pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="34fca-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="34fca-105">Nie wywołuj tej metody podczas tworzenia niezwiązanych modułów.</span><span class="sxs-lookup"><span data-stu-id="34fca-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34fca-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="34fca-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="34fca-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="34fca-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="34fca-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="34fca-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34fca-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="34fca-109">Return Value</span></span>  
 <span data-ttu-id="34fca-110">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="34fca-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34fca-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34fca-111">Requirements</span></span>  
 <span data-ttu-id="34fca-112">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="34fca-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34fca-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34fca-113">See also</span></span>

- [<span data-ttu-id="34fca-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="34fca-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="34fca-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="34fca-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="34fca-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="34fca-116">ALink API</span></span>](index.md)
