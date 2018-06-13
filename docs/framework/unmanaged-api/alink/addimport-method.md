---
title: AddImport metoda1
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
ms.openlocfilehash: 98fefc0240f6496a3e7bfb491e27a57e98cfea1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404069"
---
# <a name="addimport-method1"></a><span data-ttu-id="8b5ef-102">AddImport metoda1</span><span class="sxs-lookup"><span data-stu-id="8b5ef-102">AddImport Method1</span></span>
<span data-ttu-id="8b5ef-103">Dodaje importów do zestawu.</span><span class="sxs-lookup"><span data-stu-id="8b5ef-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b5ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b5ef-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b5ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b5ef-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8b5ef-106">Unikatowy identyfikator zestawu zostać rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="8b5ef-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="8b5ef-107">Unikatowy identyfikator pobierany z [ImportFile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="8b5ef-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8b5ef-108">COM + FileDef flagi, takich jak `ffContainsNoMetaData` i `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="8b5ef-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="8b5ef-109">`dwFlags` jest przekazywana do [DefineFile — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="8b5ef-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="8b5ef-110">Wskaźnik do tokenu, który odbiera identyfikator wynikowy plik.</span><span class="sxs-lookup"><span data-stu-id="8b5ef-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b5ef-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8b5ef-111">Return Value</span></span>  
 <span data-ttu-id="8b5ef-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8b5ef-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b5ef-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b5ef-113">Requirements</span></span>  
 <span data-ttu-id="8b5ef-114">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="8b5ef-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5ef-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b5ef-115">See Also</span></span>  
 [<span data-ttu-id="8b5ef-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b5ef-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="8b5ef-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b5ef-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="8b5ef-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="8b5ef-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
