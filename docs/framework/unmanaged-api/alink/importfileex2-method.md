---
title: ImportFileEx2 — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
ms.openlocfilehash: 7e270dbfc63c03e77cb4b0694296e48c2035b8a6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445691"
---
# <a name="importfileex2-method"></a><span data-ttu-id="949e4-102">ImportFileEx2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="949e4-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="949e4-103">Importuje zestawy i niepowiązane moduły.</span><span class="sxs-lookup"><span data-stu-id="949e4-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="949e4-104">Ta metoda jest taka sama jak [Metoda ImportFile —](importfile-method.md), ale działa nawet wtedy, gdy importowany plik nie istnieje na dysku.</span><span class="sxs-lookup"><span data-stu-id="949e4-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="949e4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="949e4-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="949e4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="949e4-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="949e4-107">Nazwa pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="949e4-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="949e4-108">Opcjonalna nazwa pliku docelowego.</span><span class="sxs-lookup"><span data-stu-id="949e4-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="949e4-109">Opcjonalny interfejs [interfejsu IMetaDataAssemblyImportgo](../metadata/imetadataassemblyimport-interface.md) zakresu importu.</span><span class="sxs-lookup"><span data-stu-id="949e4-109">Optional import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="949e4-110">Jeśli wartość jest równa TRUE, używane są wartości, w przeciwnym razie importowanie należy wykonać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="949e4-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="949e4-111">Flagi do przesłania do [metody OpenScope —](../metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="949e4-111">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="949e4-112">Odbiera unikatowy identyfikator zestawu lub pliku.</span><span class="sxs-lookup"><span data-stu-id="949e4-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="949e4-113">Odbiera Interfejs [IMetaDataAssemblyImporty](../metadata/imetadataassemblyimport-interface.md) zakresu importu zestawu.</span><span class="sxs-lookup"><span data-stu-id="949e4-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="949e4-114">Może mieć wartość NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="949e4-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="949e4-115">Odbiera liczbę zaimportowanych plików i/lub zakresów.</span><span class="sxs-lookup"><span data-stu-id="949e4-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="949e4-116">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="949e4-116">Return Value</span></span>  
 <span data-ttu-id="949e4-117">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="949e4-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="949e4-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="949e4-118">Requirements</span></span>  
 <span data-ttu-id="949e4-119">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="949e4-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="949e4-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="949e4-120">See also</span></span>

- [<span data-ttu-id="949e4-121">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="949e4-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="949e4-122">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="949e4-122">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="949e4-123">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="949e4-123">ALink API</span></span>](index.md)
