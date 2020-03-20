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
ms.openlocfilehash: 5a8442b1f0869e1592a05dfeeb0f5e6d583f3ea8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179390"
---
# <a name="setpekind-method"></a><span data-ttu-id="b10a3-102">SetPEKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="b10a3-102">SetPEKind Method</span></span>
<span data-ttu-id="b10a3-103">Określa typ pliku wykonywalnego przenośnego, specyficznego dla komputera lub niezależnego od komputera.</span><span class="sxs-lookup"><span data-stu-id="b10a3-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b10a3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b10a3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="b10a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b10a3-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b10a3-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="b10a3-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="b10a3-107">Token pliku, dla którego ma być ustawiony typ PE.</span><span class="sxs-lookup"><span data-stu-id="b10a3-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="b10a3-108">Może mieć `AssemblyID` wartość NULL, jeśli nie oznacza niezwiązanego trybu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="b10a3-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="b10a3-109">Typ PE, wskazany przez [wyliczenie CorPEKind](../metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b10a3-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="b10a3-110">Architektura komputera docelowego, jak wskazano w nagłówku NT.</span><span class="sxs-lookup"><span data-stu-id="b10a3-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b10a3-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b10a3-111">Return Value</span></span>  
 <span data-ttu-id="b10a3-112">Zwraca S_OK, jeśli metoda powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="b10a3-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b10a3-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b10a3-113">Requirements</span></span>  
 <span data-ttu-id="b10a3-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="b10a3-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b10a3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b10a3-115">See also</span></span>

- [<span data-ttu-id="b10a3-116">GetPEKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="b10a3-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="b10a3-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b10a3-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b10a3-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="b10a3-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b10a3-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="b10a3-119">ALink API</span></span>](index.md)
