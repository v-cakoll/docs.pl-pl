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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1c950e9a6e53e04cc0f2e52a140612562b32ff1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776984"
---
# <a name="importfileex2-method"></a><span data-ttu-id="e4a34-102">ImportFileEx2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="e4a34-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="e4a34-103">Importuje zestawy i niepowiązane moduły.</span><span class="sxs-lookup"><span data-stu-id="e4a34-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="e4a34-104">Ta metoda jest taka sama jak [Metoda ImportFile —](importfile-method.md), ale działa nawet wtedy, gdy importowany plik nie istnieje na dysku.</span><span class="sxs-lookup"><span data-stu-id="e4a34-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4a34-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4a34-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e4a34-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4a34-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="e4a34-107">Nazwa pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="e4a34-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="e4a34-108">Opcjonalna nazwa pliku docelowego.</span><span class="sxs-lookup"><span data-stu-id="e4a34-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="e4a34-109">Opcjonalny interfejs [interfejsu IMetaDataAssemblyImportgo](../metadata/imetadataassemblyimport-interface.md) zakresu importu.</span><span class="sxs-lookup"><span data-stu-id="e4a34-109">Optional import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="e4a34-110">Jeśli wartość jest równa TRUE, używane są wartości, w przeciwnym razie importowanie należy wykonać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="e4a34-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="e4a34-111">Flagi do przesłania do [metody OpenScope —](../metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="e4a34-111">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="e4a34-112">Odbiera unikatowy identyfikator zestawu lub pliku.</span><span class="sxs-lookup"><span data-stu-id="e4a34-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="e4a34-113">Odbiera Interfejs [IMetaDataAssemblyImporty](../metadata/imetadataassemblyimport-interface.md) zakresu importu zestawu.</span><span class="sxs-lookup"><span data-stu-id="e4a34-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="e4a34-114">Może mieć wartość NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="e4a34-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="e4a34-115">Odbiera liczbę zaimportowanych plików i/lub zakresów.</span><span class="sxs-lookup"><span data-stu-id="e4a34-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4a34-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e4a34-116">Return Value</span></span>  
 <span data-ttu-id="e4a34-117">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e4a34-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4a34-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4a34-118">Requirements</span></span>  
 <span data-ttu-id="e4a34-119">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="e4a34-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a34-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4a34-120">See also</span></span>

- [<span data-ttu-id="e4a34-121">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4a34-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e4a34-122">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4a34-122">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e4a34-123">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="e4a34-123">ALink API</span></span>](index.md)
