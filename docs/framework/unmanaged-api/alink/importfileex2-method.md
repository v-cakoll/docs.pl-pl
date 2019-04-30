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
ms.openlocfilehash: 784e58e0c5c2329705671580d53763f2ac30f0b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753492"
---
# <a name="importfileex2-method"></a><span data-ttu-id="dfa2b-102">ImportFileEx2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="dfa2b-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="dfa2b-103">Importuje zestawów i modułów niepowiązanej.</span><span class="sxs-lookup"><span data-stu-id="dfa2b-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="dfa2b-104">Ta metoda przypomina [importfile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ale wtedy, gdy importowanego pliku nie istnieje na dysku.</span><span class="sxs-lookup"><span data-stu-id="dfa2b-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa2b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfa2b-105">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="dfa2b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfa2b-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="dfa2b-107">Nazwa pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="dfa2b-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="dfa2b-108">Opcjonalna nazwa pliku docelowego.</span><span class="sxs-lookup"><span data-stu-id="dfa2b-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="dfa2b-109">Zakres opcjonalny import [imetadataassemblyimport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dfa2b-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="dfa2b-110">W przypadku opcji TRUE importtypes — jest używana, w przeciwnym razie importowanie muszą być wykonywane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="dfa2b-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="dfa2b-111">Flagi, aby być przekazywane do [openscope — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="dfa2b-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="dfa2b-112">Otrzymuje unikatowy identyfikator zestawu lub pliku.</span><span class="sxs-lookup"><span data-stu-id="dfa2b-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="dfa2b-113">Odbiera zakresu importu zestawu [imetadataassemblyimport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dfa2b-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="dfa2b-114">Może mieć wartości NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="dfa2b-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="dfa2b-115">Odbiera liczbę plików i/lub zakresów zaimportowane.</span><span class="sxs-lookup"><span data-stu-id="dfa2b-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfa2b-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dfa2b-116">Return Value</span></span>  
 <span data-ttu-id="dfa2b-117">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="dfa2b-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfa2b-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dfa2b-118">Requirements</span></span>  
 <span data-ttu-id="dfa2b-119">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="dfa2b-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa2b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dfa2b-120">See also</span></span>

- [<span data-ttu-id="dfa2b-121">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="dfa2b-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="dfa2b-122">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="dfa2b-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="dfa2b-123">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="dfa2b-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
