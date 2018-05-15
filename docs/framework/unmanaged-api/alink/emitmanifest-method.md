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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6df28cd3eaadfe62cd34e20e6e03d5a89e6bb425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="emitmanifest-method"></a><span data-ttu-id="c57b4-102">EmitManifest — Metoda</span><span class="sxs-lookup"><span data-stu-id="c57b4-102">EmitManifest Method</span></span>
<span data-ttu-id="c57b4-103">Emituje końcowego manifestu.</span><span class="sxs-lookup"><span data-stu-id="c57b4-103">Emits the final manifest.</span></span> <span data-ttu-id="c57b4-104">Tę metodę można wywołać po zaimportowaniu wszystkie inne pliki i ustawieniu wszystkich opcji.</span><span class="sxs-lookup"><span data-stu-id="c57b4-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="c57b4-105">Nie wywołuj tej metody dla modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="c57b4-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c57b4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c57b4-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c57b4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c57b4-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c57b4-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="c57b4-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="c57b4-109">Odbiera rozmiar do zarezerwowania w pliku zestawu pobierane z [StrongNameSignatureSize — funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="c57b4-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="c57b4-110">Opcjonalnie otrzymuje token manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="c57b4-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c57b4-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c57b4-111">Return Value</span></span>  
 <span data-ttu-id="c57b4-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c57b4-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c57b4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c57b4-113">Requirements</span></span>  
 <span data-ttu-id="c57b4-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="c57b4-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c57b4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c57b4-115">See Also</span></span>  
 [<span data-ttu-id="c57b4-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="c57b4-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c57b4-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c57b4-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c57b4-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="c57b4-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
