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
ms.openlocfilehash: 589bd7b2132693c89dc10ae1a5c8d0bf52ed481e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218995"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="f57b0-102">SetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="f57b0-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="f57b0-103">Przypisuje właściwości na poziomie zestawu.</span><span class="sxs-lookup"><span data-stu-id="f57b0-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f57b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f57b0-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f57b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f57b0-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f57b0-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="f57b0-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f57b0-107">Plik, który definiuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="f57b0-107">File that defines the property.</span></span> <span data-ttu-id="f57b0-108">Może mieć wartości NULL, jeśli `AssemblyID` nie wskazuje niepowiązanych modułu netmodule.</span><span class="sxs-lookup"><span data-stu-id="f57b0-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="f57b0-109">Wskazuje opcję modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="f57b0-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="f57b0-110">Nowa wartość opcji.</span><span class="sxs-lookup"><span data-stu-id="f57b0-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f57b0-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f57b0-111">Return Value</span></span>  
 <span data-ttu-id="f57b0-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f57b0-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f57b0-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f57b0-113">Requirements</span></span>  
 <span data-ttu-id="f57b0-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="f57b0-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f57b0-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f57b0-115">See also</span></span>

- [<span data-ttu-id="f57b0-116">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f57b0-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f57b0-117">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f57b0-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f57b0-118">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="f57b0-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
