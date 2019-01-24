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
ms.openlocfilehash: 9217a045a8ddf6ad41adcc71a9568a05fe3fb334
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565552"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="55e81-102">EmitManifest — Metoda</span><span class="sxs-lookup"><span data-stu-id="55e81-102">EmitManifest Method</span></span>
<span data-ttu-id="55e81-103">Emituje końcowego manifestu.</span><span class="sxs-lookup"><span data-stu-id="55e81-103">Emits the final manifest.</span></span> <span data-ttu-id="55e81-104">Po zaimportowaniu wszystkich innych plików i ustawieniu wszystkich opcji, należy wywołać tę metodę.</span><span class="sxs-lookup"><span data-stu-id="55e81-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="55e81-105">Nie wywołuj tej metody dla modułów niepowiązanej.</span><span class="sxs-lookup"><span data-stu-id="55e81-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55e81-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="55e81-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55e81-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="55e81-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="55e81-108">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="55e81-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="55e81-109">Odbiera rozmiar do zarezerwowania w pliku zestawu pobierane [strongnamesignaturesize — funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="55e81-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="55e81-110">Opcjonalnie odbiera token manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="55e81-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55e81-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="55e81-111">Return Value</span></span>  
 <span data-ttu-id="55e81-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="55e81-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55e81-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="55e81-113">Requirements</span></span>  
 <span data-ttu-id="55e81-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="55e81-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55e81-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55e81-115">See also</span></span>
- [<span data-ttu-id="55e81-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="55e81-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="55e81-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="55e81-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="55e81-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="55e81-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
