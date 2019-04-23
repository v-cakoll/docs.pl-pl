---
title: ImportFile — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69e48c6c3179ced167fdc39ae4df859f161727ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077254"
---
# <a name="importfile-method"></a><span data-ttu-id="a669f-102">ImportFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="a669f-102">ImportFile Method</span></span>
<span data-ttu-id="a669f-103">Importuje zestawów i modułów niepowiązanej.</span><span class="sxs-lookup"><span data-stu-id="a669f-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a669f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a669f-104">Syntax</span></span>  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a669f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a669f-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="a669f-106">W pełni kwalifikowana nazwa pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="a669f-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="a669f-107">Nazwa pliku wyjściowego opcjonalny, którego można zmienić nazwy pliku, ponieważ jest on połączony do zestawu.</span><span class="sxs-lookup"><span data-stu-id="a669f-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="a669f-108">W przypadku opcji TRUE importtypes — jest używana, w przeciwnym razie importowanie muszą być wykonywane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="a669f-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="a669f-109">Wskaźnik do tokenu, gdzie będą przechowywane Unikatowy identyfikator pliku.</span><span class="sxs-lookup"><span data-stu-id="a669f-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="a669f-110">Plik może być zestawu lub pliku.</span><span class="sxs-lookup"><span data-stu-id="a669f-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="a669f-111">Otrzymuje wskaźnik do [imetadataassemblyimport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a669f-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="a669f-112">Może mieć wartości NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="a669f-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="a669f-113">Wskaźnik do liczby plików i/lub zakresy, które zostały zaimportowane.</span><span class="sxs-lookup"><span data-stu-id="a669f-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a669f-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a669f-114">Return Value</span></span>  
 <span data-ttu-id="a669f-115">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="a669f-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a669f-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a669f-116">Requirements</span></span>  
 <span data-ttu-id="a669f-117">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="a669f-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a669f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a669f-118">See also</span></span>

- [<span data-ttu-id="a669f-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="a669f-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="a669f-120">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a669f-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="a669f-121">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="a669f-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
