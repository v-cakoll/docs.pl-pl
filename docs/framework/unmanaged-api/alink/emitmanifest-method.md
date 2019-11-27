---
title: EmitManifest — Metoda
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
ms.openlocfilehash: f3bb978b8358992fd9aa7da922e28efc1ed1a951
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446480"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="ed626-102">EmitManifest — Metoda</span><span class="sxs-lookup"><span data-stu-id="ed626-102">EmitManifest Method</span></span>
<span data-ttu-id="ed626-103">Emituje końcowy manifest.</span><span class="sxs-lookup"><span data-stu-id="ed626-103">Emits the final manifest.</span></span> <span data-ttu-id="ed626-104">Wywołaj tę metodę po zaimportowaniu wszystkich pozostałych plików i ustawieniu wszystkich opcji.</span><span class="sxs-lookup"><span data-stu-id="ed626-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="ed626-105">Nie wywołuj tej metody dla modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="ed626-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed626-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed626-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed626-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed626-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ed626-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="ed626-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="ed626-109">Odbiera rozmiar do zarezerwowania w pliku zestawu pobranym z [funkcji StrongNameSignatureSize —](../strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="ed626-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="ed626-110">Opcjonalnie odbiera token manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="ed626-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed626-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ed626-111">Return Value</span></span>  
 <span data-ttu-id="ed626-112">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ed626-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed626-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed626-113">Requirements</span></span>  
 <span data-ttu-id="ed626-114">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="ed626-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed626-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed626-115">See also</span></span>

- [<span data-ttu-id="ed626-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed626-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ed626-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed626-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ed626-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="ed626-118">ALink API</span></span>](index.md)
