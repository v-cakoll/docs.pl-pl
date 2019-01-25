---
title: AddFile, metoda1
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
ms.openlocfilehash: 84b68638ed0f7a86156cf7e5fcc98d3c02cba18a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662611"
---
# <a name="addfile-method1"></a><span data-ttu-id="6eb00-102">AddFile, metoda1</span><span class="sxs-lookup"><span data-stu-id="6eb00-102">AddFile Method1</span></span>
<span data-ttu-id="6eb00-103">Dodaje pliki do zestawu.</span><span class="sxs-lookup"><span data-stu-id="6eb00-103">Adds files to the assembly.</span></span> <span data-ttu-id="6eb00-104">Można również utworzyć niezwiązanego moduły.</span><span class="sxs-lookup"><span data-stu-id="6eb00-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb00-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6eb00-105">Syntax</span></span>  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6eb00-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6eb00-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6eb00-107">Unikatowy identyfikator zestawie, który ma zostać rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="6eb00-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="6eb00-108">W pełni kwalifikowana nazwa pliku ma zostać dodana.</span><span class="sxs-lookup"><span data-stu-id="6eb00-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6eb00-109">COM + FileDef flagi, takich jak `ffContainsNoMetaData` i `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="6eb00-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="6eb00-110">`dwFlags` jest przekazywany do [definefile — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="6eb00-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="6eb00-111">[IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interfejs służący do emitowania metadanych, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="6eb00-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="6eb00-112">Wskaźnik do przechowywania Unikatowy identyfikator dodany plik.</span><span class="sxs-lookup"><span data-stu-id="6eb00-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6eb00-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6eb00-113">Return Value</span></span>  
 <span data-ttu-id="6eb00-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6eb00-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eb00-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6eb00-115">Requirements</span></span>  
 <span data-ttu-id="6eb00-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="6eb00-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb00-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6eb00-117">See also</span></span>
- [<span data-ttu-id="6eb00-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="6eb00-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="6eb00-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6eb00-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="6eb00-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="6eb00-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
