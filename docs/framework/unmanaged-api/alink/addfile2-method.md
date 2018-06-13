---
title: AddFile2 — Metoda
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4735103f277d710dd23adfa19c475c425feaa36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403334"
---
# <a name="addfile2-method"></a><span data-ttu-id="eb207-102">AddFile2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="eb207-102">AddFile2 Method</span></span>
<span data-ttu-id="eb207-103">Dodaje pliki do zestawu.</span><span class="sxs-lookup"><span data-stu-id="eb207-103">Adds files to the assembly.</span></span> <span data-ttu-id="eb207-104">Można również utworzyć niezwiązanego moduły.</span><span class="sxs-lookup"><span data-stu-id="eb207-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb207-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb207-105">Syntax</span></span>  
  
```  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb207-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb207-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="eb207-107">Identyfikator zestawu, do którego zostanie dodany plik.</span><span class="sxs-lookup"><span data-stu-id="eb207-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="eb207-108">Nazwa pliku do dodania.</span><span class="sxs-lookup"><span data-stu-id="eb207-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="eb207-109">COM + `FileDef` flagi, takich jak `ffContainsNoMetaData` i `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="eb207-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="eb207-110">`dwFlags` jest przekazywana do [DefineFile — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="eb207-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="eb207-111">Interfejs do [IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="eb207-111">Interface to [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="eb207-112">Odbiera identyfikator pliku dodawany.</span><span class="sxs-lookup"><span data-stu-id="eb207-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb207-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="eb207-113">Return Value</span></span>  
 <span data-ttu-id="eb207-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="eb207-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb207-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb207-115">Requirements</span></span>  
 <span data-ttu-id="eb207-116">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="eb207-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb207-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb207-117">See Also</span></span>  
 [<span data-ttu-id="eb207-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb207-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="eb207-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb207-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="eb207-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="eb207-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
