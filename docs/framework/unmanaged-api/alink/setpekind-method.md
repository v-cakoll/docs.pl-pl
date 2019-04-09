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
ms.openlocfilehash: dec04fa267c61798a3340e9d1e18150b812e9eaf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092659"
---
# <a name="setpekind-method"></a><span data-ttu-id="d6c2f-102">SetPEKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="d6c2f-102">SetPEKind Method</span></span>
<span data-ttu-id="d6c2f-103">Określa typ przenośnego pliku wykonywalnego, specyficzny dla komputera lub niezależny od maszyny.</span><span class="sxs-lookup"><span data-stu-id="d6c2f-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c2f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6c2f-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="d6c2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6c2f-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d6c2f-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="d6c2f-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d6c2f-107">Token pliku, dla którego ma można ustawić typu PE.</span><span class="sxs-lookup"><span data-stu-id="d6c2f-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="d6c2f-108">Może mieć wartości NULL, jeśli `AssemblyID` nie wskazuje niepowiązanych modułu netmodule.</span><span class="sxs-lookup"><span data-stu-id="d6c2f-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="d6c2f-109">Typ PE, wskazane przez [corpekind — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="d6c2f-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="d6c2f-110">Architektura maszyny docelowej, jak wskazano w nagłówku NT.</span><span class="sxs-lookup"><span data-stu-id="d6c2f-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6c2f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d6c2f-111">Return Value</span></span>  
 <span data-ttu-id="d6c2f-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d6c2f-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6c2f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6c2f-113">Requirements</span></span>  
 <span data-ttu-id="d6c2f-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="d6c2f-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c2f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6c2f-115">See also</span></span>

- [<span data-ttu-id="d6c2f-116">GetPEKind, metoda</span><span class="sxs-lookup"><span data-stu-id="d6c2f-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="d6c2f-117">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d6c2f-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d6c2f-118">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d6c2f-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d6c2f-119">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="d6c2f-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
