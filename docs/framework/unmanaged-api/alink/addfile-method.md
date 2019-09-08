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
ms.openlocfilehash: b1406c68f1f6abff4d140b131f5f630d0fd767e1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787689"
---
# <a name="addfile-method"></a><span data-ttu-id="739ac-102">AddFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="739ac-102">AddFile Method</span></span>
<span data-ttu-id="739ac-103">Dodaje pliki do zestawu.</span><span class="sxs-lookup"><span data-stu-id="739ac-103">Adds files to the assembly.</span></span> <span data-ttu-id="739ac-104">Może również służyć do tworzenia niezwiązanych modułów.</span><span class="sxs-lookup"><span data-stu-id="739ac-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="739ac-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="739ac-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="739ac-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="739ac-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="739ac-107">Unikatowy identyfikator zestawu, który ma zostać rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="739ac-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="739ac-108">W pełni kwalifikowana nazwa pliku, który ma zostać dodany.</span><span class="sxs-lookup"><span data-stu-id="739ac-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="739ac-109">Flagi FileDef modelu COM+, `ffContainsNoMetaData` takie `ffWriteable`jak i.</span><span class="sxs-lookup"><span data-stu-id="739ac-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="739ac-110">`dwFlags`jest przenoszona do [metody DefineFile —](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="739ac-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="739ac-111">Interfejs [interfejsu IMetaDataEmit](../metadata/imetadataemit-interface.md) , który ma być używany do emitowania metadanych, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="739ac-111">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="739ac-112">Wskaźnik do lokalizacji, w której będzie przechowywany unikatowy identyfikator dodanego pliku.</span><span class="sxs-lookup"><span data-stu-id="739ac-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="739ac-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="739ac-113">Return Value</span></span>  
 <span data-ttu-id="739ac-114">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="739ac-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="739ac-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="739ac-115">Requirements</span></span>  
 <span data-ttu-id="739ac-116">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="739ac-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="739ac-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="739ac-117">See also</span></span>

- [<span data-ttu-id="739ac-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="739ac-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="739ac-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="739ac-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="739ac-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="739ac-120">ALink API</span></span>](index.md)
