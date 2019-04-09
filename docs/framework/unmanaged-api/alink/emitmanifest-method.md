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
ms.openlocfilehash: 051b5f47db05301f3a3326a2cc4cc5cf5c8b1ec2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137829"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="04731-102">EmitManifest — Metoda</span><span class="sxs-lookup"><span data-stu-id="04731-102">EmitManifest Method</span></span>
<span data-ttu-id="04731-103">Emituje końcowego manifestu.</span><span class="sxs-lookup"><span data-stu-id="04731-103">Emits the final manifest.</span></span> <span data-ttu-id="04731-104">Po zaimportowaniu wszystkich innych plików i ustawieniu wszystkich opcji, należy wywołać tę metodę.</span><span class="sxs-lookup"><span data-stu-id="04731-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="04731-105">Nie wywołuj tej metody dla modułów niepowiązanej.</span><span class="sxs-lookup"><span data-stu-id="04731-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04731-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="04731-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="04731-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="04731-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="04731-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="04731-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="04731-109">Odbiera rozmiar do zarezerwowania w pliku zestawu pobierane [strongnamesignaturesize — funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="04731-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="04731-110">Opcjonalnie odbiera token manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="04731-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04731-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="04731-111">Return Value</span></span>  
 <span data-ttu-id="04731-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="04731-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04731-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04731-113">Requirements</span></span>  
 <span data-ttu-id="04731-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="04731-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04731-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04731-115">See also</span></span>

- [<span data-ttu-id="04731-116">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="04731-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="04731-117">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="04731-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="04731-118">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="04731-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
