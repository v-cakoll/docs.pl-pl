---
title: AddFile — Metoda
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 056d1ac0ffd3ad7fa7cb1f86ae13331ac38b3eff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775651"
---
# <a name="addfile-method"></a><span data-ttu-id="0fd5b-102">AddFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="0fd5b-102">AddFile Method</span></span>
<span data-ttu-id="0fd5b-103">Dodaje pliki do zestawu.</span><span class="sxs-lookup"><span data-stu-id="0fd5b-103">Adds files to the assembly.</span></span> <span data-ttu-id="0fd5b-104">Można również utworzyć niezwiązanego moduły.</span><span class="sxs-lookup"><span data-stu-id="0fd5b-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fd5b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fd5b-105">Syntax</span></span>  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fd5b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fd5b-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0fd5b-107">Unikatowy identyfikator zestawie, który ma zostać rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="0fd5b-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="0fd5b-108">W pełni kwalifikowana nazwa pliku ma zostać dodana.</span><span class="sxs-lookup"><span data-stu-id="0fd5b-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0fd5b-109">COM + FileDef flagi, takich jak `ffContainsNoMetaData` i `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="0fd5b-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="0fd5b-110">`dwFlags` jest przekazywany do [definefile — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="0fd5b-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="0fd5b-111">[IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interfejs służący do emitowania metadanych, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="0fd5b-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="0fd5b-112">Wskaźnik do przechowywania Unikatowy identyfikator dodany plik.</span><span class="sxs-lookup"><span data-stu-id="0fd5b-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0fd5b-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0fd5b-113">Return Value</span></span>  
 <span data-ttu-id="0fd5b-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="0fd5b-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fd5b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0fd5b-115">Requirements</span></span>  
 <span data-ttu-id="0fd5b-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="0fd5b-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd5b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fd5b-117">See also</span></span>

- [<span data-ttu-id="0fd5b-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="0fd5b-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="0fd5b-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0fd5b-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="0fd5b-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="0fd5b-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
