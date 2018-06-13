---
title: SetPEKind — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b985aeb97621e552e9e97581e67cae029d019ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405896"
---
# <a name="setpekind-method"></a><span data-ttu-id="88ee3-102">SetPEKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="88ee3-102">SetPEKind Method</span></span>
<span data-ttu-id="88ee3-103">Określa typ przenośnego pliku wykonywalnego, komputera lub pochodzącego od dowolnego komputera.</span><span class="sxs-lookup"><span data-stu-id="88ee3-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88ee3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88ee3-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="88ee3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88ee3-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="88ee3-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="88ee3-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="88ee3-107">Token pliku, dla którego należy ustawić typ PE.</span><span class="sxs-lookup"><span data-stu-id="88ee3-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="88ee3-108">Może mieć wartość NULL, jeśli `AssemblyID` nie wskazuje niezwiązanego modułu netmodule.</span><span class="sxs-lookup"><span data-stu-id="88ee3-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="88ee3-109">Typ środowiska Preinstalacyjnego wskazywany przez [CorPEKind — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="88ee3-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="88ee3-110">Architektura komputera docelowego, jak wskazano w nagłówku NT.</span><span class="sxs-lookup"><span data-stu-id="88ee3-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88ee3-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="88ee3-111">Return Value</span></span>  
 <span data-ttu-id="88ee3-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="88ee3-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88ee3-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88ee3-113">Requirements</span></span>  
 <span data-ttu-id="88ee3-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="88ee3-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88ee3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88ee3-115">See Also</span></span>  
 [<span data-ttu-id="88ee3-116">GetPEKind, metoda</span><span class="sxs-lookup"><span data-stu-id="88ee3-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)  
 [<span data-ttu-id="88ee3-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="88ee3-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="88ee3-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="88ee3-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="88ee3-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="88ee3-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
