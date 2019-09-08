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
ms.openlocfilehash: c3a6892dbed172c0be3b036014d393657dbc8593
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777520"
---
# <a name="addfile2-method"></a><span data-ttu-id="7d109-102">AddFile2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="7d109-102">AddFile2 Method</span></span>
<span data-ttu-id="7d109-103">Dodaje pliki do zestawu.</span><span class="sxs-lookup"><span data-stu-id="7d109-103">Adds files to the assembly.</span></span> <span data-ttu-id="7d109-104">Może również służyć do tworzenia niezwiązanych modułów.</span><span class="sxs-lookup"><span data-stu-id="7d109-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d109-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d109-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d109-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d109-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7d109-107">Identyfikator zestawu, do którego zostanie dodany plik.</span><span class="sxs-lookup"><span data-stu-id="7d109-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="7d109-108">Nazwa pliku, który ma zostać dodany.</span><span class="sxs-lookup"><span data-stu-id="7d109-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7d109-109">Flagi `FileDef` com+, takie `ffContainsNoMetaData` jak `ffWriteable`i.</span><span class="sxs-lookup"><span data-stu-id="7d109-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="7d109-110">`dwFlags`jest przenoszona do [metody DefineFile —](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="7d109-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="7d109-111">Interfejs do interfejsu [interfejsu IMetaDataEmit2](../metadata/imetadataemit2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7d109-111">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="7d109-112">Odbiera identyfikator dodawanego pliku.</span><span class="sxs-lookup"><span data-stu-id="7d109-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d109-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7d109-113">Return Value</span></span>  
 <span data-ttu-id="7d109-114">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7d109-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d109-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d109-115">Requirements</span></span>  
 <span data-ttu-id="7d109-116">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="7d109-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d109-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d109-117">See also</span></span>

- [<span data-ttu-id="7d109-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d109-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="7d109-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d109-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="7d109-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="7d109-120">ALink API</span></span>](index.md)
