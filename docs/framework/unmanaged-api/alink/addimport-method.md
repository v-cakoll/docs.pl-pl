---
title: AddImport — Metoda
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95a434cc365e12aa19d164951726ddad8945f60d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974136"
---
# <a name="addimport-method"></a><span data-ttu-id="a153b-102">AddImport — Metoda</span><span class="sxs-lookup"><span data-stu-id="a153b-102">AddImport Method</span></span>
<span data-ttu-id="a153b-103">Importy dodaje do zestawu.</span><span class="sxs-lookup"><span data-stu-id="a153b-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a153b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a153b-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a153b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a153b-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a153b-106">Unikatowy identyfikator zestawu, aby zostać rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="a153b-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="a153b-107">Unikatowy identyfikator, pobierane z [importfile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="a153b-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a153b-108">COM + FileDef flagi, takich jak `ffContainsNoMetaData` i `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="a153b-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="a153b-109">`dwFlags` jest przekazywany do [definefile — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="a153b-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="a153b-110">Wskaźnik do tokenu, który odbiera identyfikator wynikowy plik.</span><span class="sxs-lookup"><span data-stu-id="a153b-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a153b-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a153b-111">Return Value</span></span>  
 <span data-ttu-id="a153b-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a153b-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a153b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a153b-113">Requirements</span></span>  
 <span data-ttu-id="a153b-114">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="a153b-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a153b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a153b-115">See also</span></span>
- [<span data-ttu-id="a153b-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="a153b-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="a153b-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a153b-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="a153b-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="a153b-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
