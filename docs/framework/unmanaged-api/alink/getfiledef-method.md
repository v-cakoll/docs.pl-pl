---
title: GetFileDef — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
ms.openlocfilehash: 6a561205602920123176bd421ca2ef1b601166c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426047"
---
# <a name="getfiledef-method"></a><span data-ttu-id="7e798-102">GetFileDef — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e798-102">GetFileDef Method</span></span>
<span data-ttu-id="7e798-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span><span class="sxs-lookup"><span data-stu-id="7e798-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e798-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e798-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e798-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e798-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7e798-106">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="7e798-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="7e798-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span><span class="sxs-lookup"><span data-stu-id="7e798-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="7e798-108">Receives the FileDef token.</span><span class="sxs-lookup"><span data-stu-id="7e798-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e798-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7e798-109">Return Value</span></span>  
 <span data-ttu-id="7e798-110">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="7e798-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e798-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e798-111">Requirements</span></span>  
 <span data-ttu-id="7e798-112">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="7e798-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e798-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e798-113">See also</span></span>

- [<span data-ttu-id="7e798-114">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e798-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="7e798-115">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e798-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="7e798-116">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="7e798-116">ALink API</span></span>](index.md)
