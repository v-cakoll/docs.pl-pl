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
ms.openlocfilehash: 7ff6bde5009e834bfca156fe4d3ad16da53ded85
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742387"
---
# <a name="addfile-method"></a><span data-ttu-id="a553c-102">AddFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="a553c-102">AddFile Method</span></span>
<span data-ttu-id="a553c-103">Dodaje pliki do zestawu.</span><span class="sxs-lookup"><span data-stu-id="a553c-103">Adds files to the assembly.</span></span> <span data-ttu-id="a553c-104">Można również utworzyć niezwiązanego moduły.</span><span class="sxs-lookup"><span data-stu-id="a553c-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a553c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a553c-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a553c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a553c-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a553c-107">Unikatowy identyfikator zestawie, który ma zostać rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="a553c-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="a553c-108">W pełni kwalifikowana nazwa pliku ma zostać dodana.</span><span class="sxs-lookup"><span data-stu-id="a553c-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a553c-109">COM + FileDef flagi, takich jak `ffContainsNoMetaData` i `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="a553c-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="a553c-110">`dwFlags` jest przekazywany do [definefile — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="a553c-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="a553c-111">[IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interfejs służący do emitowania metadanych, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="a553c-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="a553c-112">Wskaźnik do przechowywania Unikatowy identyfikator dodany plik.</span><span class="sxs-lookup"><span data-stu-id="a553c-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a553c-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a553c-113">Return Value</span></span>  
 <span data-ttu-id="a553c-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a553c-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a553c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a553c-115">Requirements</span></span>  
 <span data-ttu-id="a553c-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="a553c-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a553c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a553c-117">See also</span></span>

- [<span data-ttu-id="a553c-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="a553c-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="a553c-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a553c-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="a553c-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="a553c-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
