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
ms.openlocfilehash: 9a48dbd38d357b668c2794ae6305ceb9cad3dcf4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787193"
---
# <a name="setpekind-method"></a><span data-ttu-id="ddff2-102">SetPEKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="ddff2-102">SetPEKind Method</span></span>
<span data-ttu-id="ddff2-103">Określa przenośny typ pliku wykonywalnego, dla maszyn lub maszyn-niezależny od.</span><span class="sxs-lookup"><span data-stu-id="ddff2-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddff2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddff2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="ddff2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddff2-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ddff2-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="ddff2-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ddff2-107">Token pliku, dla którego ma zostać ustawiony typ PE.</span><span class="sxs-lookup"><span data-stu-id="ddff2-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="ddff2-108">Może mieć wartość null `AssemblyID` , jeśli nie wskazuje niepowiązanego modułu.</span><span class="sxs-lookup"><span data-stu-id="ddff2-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="ddff2-109">Typ środowiska PE określony przez [Wyliczenie CorPEKind —](../metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="ddff2-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="ddff2-110">Architektura komputera docelowego, jak wskazano w nagłówku NT.</span><span class="sxs-lookup"><span data-stu-id="ddff2-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddff2-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ddff2-111">Return Value</span></span>  
 <span data-ttu-id="ddff2-112">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ddff2-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddff2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ddff2-113">Requirements</span></span>  
 <span data-ttu-id="ddff2-114">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="ddff2-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddff2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddff2-115">See also</span></span>

- [<span data-ttu-id="ddff2-116">GetPEKind, metoda</span><span class="sxs-lookup"><span data-stu-id="ddff2-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="ddff2-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ddff2-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ddff2-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="ddff2-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ddff2-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="ddff2-119">ALink API</span></span>](index.md)
