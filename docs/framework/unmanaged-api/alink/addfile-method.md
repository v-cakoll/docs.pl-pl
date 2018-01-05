---
title: AddFile metoda1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.AddFile
- AddFile
api_location: alink.dll
api_type: COM
f1_keywords: AddFile
helpviewer_keywords: AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 943ff2901ee0888860941e86d589060de729907d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="addfile-method1"></a><span data-ttu-id="d69dc-102">AddFile metoda1</span><span class="sxs-lookup"><span data-stu-id="d69dc-102">AddFile Method1</span></span>
<span data-ttu-id="d69dc-103">Dodaje pliki do zestawu.</span><span class="sxs-lookup"><span data-stu-id="d69dc-103">Adds files to the assembly.</span></span> <span data-ttu-id="d69dc-104">Można również utworzyć niezwiązanego moduły.</span><span class="sxs-lookup"><span data-stu-id="d69dc-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d69dc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d69dc-105">Syntax</span></span>  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d69dc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d69dc-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d69dc-107">Unikatowy identyfikator zestawu zostać rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="d69dc-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="d69dc-108">Pełna nazwa pliku do dodania.</span><span class="sxs-lookup"><span data-stu-id="d69dc-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d69dc-109">COM + FileDef flagi, takich jak `ffContainsNoMetaData` i `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="d69dc-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="d69dc-110">`dwFlags`jest przekazywana do [DefineFile — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="d69dc-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="d69dc-111">[IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interfejs służący do emisji metadanych, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="d69dc-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="d69dc-112">Wskaźnik do przechowywania Unikatowy identyfikator dodany plik.</span><span class="sxs-lookup"><span data-stu-id="d69dc-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d69dc-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d69dc-113">Return Value</span></span>  
 <span data-ttu-id="d69dc-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d69dc-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d69dc-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d69dc-115">Requirements</span></span>  
 <span data-ttu-id="d69dc-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="d69dc-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d69dc-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d69dc-117">See Also</span></span>  
 [<span data-ttu-id="d69dc-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="d69dc-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d69dc-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d69dc-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d69dc-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="d69dc-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
