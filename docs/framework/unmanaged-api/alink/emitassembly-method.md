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
ms.openlocfilehash: 6bbe5db75ded15f32a6ff3564e1116d40a745a65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446524"
---
# <a name="emitassembly-method"></a><span data-ttu-id="a2132-102">EmitAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2132-102">EmitAssembly Method</span></span>
<span data-ttu-id="a2132-103">Tworzy zestaw.</span><span class="sxs-lookup"><span data-stu-id="a2132-103">Creates the assembly.</span></span> <span data-ttu-id="a2132-104">Wywołaj tę metodę po zamknięciu wszystkich innych plików z wyjątkiem pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="a2132-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="a2132-105">Nie wywołuj tej metody podczas tworzenia niezwiązanych modułów.</span><span class="sxs-lookup"><span data-stu-id="a2132-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2132-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2132-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2132-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2132-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a2132-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="a2132-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2132-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a2132-109">Return Value</span></span>  
 <span data-ttu-id="a2132-110">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a2132-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2132-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2132-111">Requirements</span></span>  
 <span data-ttu-id="a2132-112">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="a2132-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2132-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2132-113">See also</span></span>

- [<span data-ttu-id="a2132-114">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2132-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a2132-115">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2132-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a2132-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="a2132-116">ALink API</span></span>](index.md)
