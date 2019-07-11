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
ms.openlocfilehash: 8fc581904351443f4368a68a653fd39b3548999a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741429"
---
# <a name="setpekind-method"></a><span data-ttu-id="fea44-102">SetPEKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="fea44-102">SetPEKind Method</span></span>
<span data-ttu-id="fea44-103">Określa typ przenośnego pliku wykonywalnego, specyficzny dla komputera lub niezależny od maszyny.</span><span class="sxs-lookup"><span data-stu-id="fea44-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fea44-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fea44-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="fea44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fea44-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="fea44-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="fea44-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="fea44-107">Token pliku, dla którego ma można ustawić typu PE.</span><span class="sxs-lookup"><span data-stu-id="fea44-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="fea44-108">Może mieć wartości NULL, jeśli `AssemblyID` nie wskazuje niepowiązanych modułu netmodule.</span><span class="sxs-lookup"><span data-stu-id="fea44-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="fea44-109">Typ PE, wskazane przez [corpekind — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="fea44-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="fea44-110">Architektura maszyny docelowej, jak wskazano w nagłówku NT.</span><span class="sxs-lookup"><span data-stu-id="fea44-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fea44-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fea44-111">Return Value</span></span>  
 <span data-ttu-id="fea44-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="fea44-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fea44-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fea44-113">Requirements</span></span>  
 <span data-ttu-id="fea44-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="fea44-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea44-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fea44-115">See also</span></span>

- [<span data-ttu-id="fea44-116">GetPEKind, metoda</span><span class="sxs-lookup"><span data-stu-id="fea44-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="fea44-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fea44-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="fea44-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="fea44-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="fea44-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="fea44-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
