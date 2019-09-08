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
ms.openlocfilehash: 180eb1a3129cfcd96668ecfee11947c15c5e0915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776911"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="302c1-102">SetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="302c1-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="302c1-103">Przypisuje właściwości na poziomie zestawu.</span><span class="sxs-lookup"><span data-stu-id="302c1-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="302c1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="302c1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="302c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="302c1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="302c1-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="302c1-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="302c1-107">Plik, który definiuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="302c1-107">File that defines the property.</span></span> <span data-ttu-id="302c1-108">Może mieć wartość null `AssemblyID` , jeśli nie wskazuje niepowiązanego modułu.</span><span class="sxs-lookup"><span data-stu-id="302c1-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="302c1-109">Wskazuje opcję do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="302c1-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="302c1-110">Nowa wartość opcji.</span><span class="sxs-lookup"><span data-stu-id="302c1-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="302c1-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="302c1-111">Return Value</span></span>  
 <span data-ttu-id="302c1-112">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="302c1-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="302c1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="302c1-113">Requirements</span></span>  
 <span data-ttu-id="302c1-114">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="302c1-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="302c1-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="302c1-115">See also</span></span>

- [<span data-ttu-id="302c1-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="302c1-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="302c1-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="302c1-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="302c1-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="302c1-118">ALink API</span></span>](index.md)
