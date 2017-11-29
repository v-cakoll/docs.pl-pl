---
title: "AddFile2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AddFile2
- IALink2.AddFile2
api_location: alink.dll
api_type: COM
f1_keywords: AddFile2
helpviewer_keywords: AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fe10a3ca8930087a52d02905534696dbb2d8fb25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="addfile2-method"></a><span data-ttu-id="02243-102">AddFile2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="02243-102">AddFile2 Method</span></span>
<span data-ttu-id="02243-103">Dodaje pliki do zestawu.</span><span class="sxs-lookup"><span data-stu-id="02243-103">Adds files to the assembly.</span></span> <span data-ttu-id="02243-104">Można również utworzyć niezwiązanego moduły.</span><span class="sxs-lookup"><span data-stu-id="02243-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02243-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="02243-105">Syntax</span></span>  
  
```  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02243-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="02243-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="02243-107">Identyfikator zestawu, do którego zostanie dodany plik.</span><span class="sxs-lookup"><span data-stu-id="02243-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="02243-108">Nazwa pliku do dodania.</span><span class="sxs-lookup"><span data-stu-id="02243-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="02243-109">COM + `FileDef` flagi, takich jak `ffContainsNoMetaData` i `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="02243-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="02243-110">`dwFlags`jest przekazywana do [DefineFile — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="02243-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="02243-111">Interfejs do [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="02243-111">Interface to [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="02243-112">Odbiera identyfikator pliku dodawany.</span><span class="sxs-lookup"><span data-stu-id="02243-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02243-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="02243-113">Return Value</span></span>  
 <span data-ttu-id="02243-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="02243-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02243-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="02243-115">Requirements</span></span>  
 <span data-ttu-id="02243-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="02243-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02243-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02243-117">See Also</span></span>  
 [<span data-ttu-id="02243-118">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="02243-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="02243-119">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="02243-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="02243-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="02243-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
