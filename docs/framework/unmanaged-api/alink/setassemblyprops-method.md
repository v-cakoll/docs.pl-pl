---
title: SetAssemblyProps — Metoda
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aed553a3a8d54b5229a122e76b61e3e58d4af3c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401969"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="59f24-102">SetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="59f24-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="59f24-103">Przypisuje poziom zestawu właściwości.</span><span class="sxs-lookup"><span data-stu-id="59f24-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59f24-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59f24-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59f24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="59f24-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="59f24-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="59f24-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="59f24-107">Plik, który definiuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="59f24-107">File that defines the property.</span></span> <span data-ttu-id="59f24-108">Może mieć wartość NULL, jeśli `AssemblyID` nie wskazuje niezwiązanego modułu netmodule.</span><span class="sxs-lookup"><span data-stu-id="59f24-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="59f24-109">Wskazuje opcję, aby zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="59f24-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="59f24-110">Nowa wartość opcji.</span><span class="sxs-lookup"><span data-stu-id="59f24-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59f24-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="59f24-111">Return Value</span></span>  
 <span data-ttu-id="59f24-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="59f24-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59f24-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59f24-113">Requirements</span></span>  
 <span data-ttu-id="59f24-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="59f24-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f24-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59f24-115">See Also</span></span>  
 [<span data-ttu-id="59f24-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="59f24-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="59f24-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="59f24-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="59f24-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="59f24-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
