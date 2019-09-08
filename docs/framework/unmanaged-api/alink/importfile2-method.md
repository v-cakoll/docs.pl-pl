---
title: ImportFile2 — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a03fc24e5ef932d13c0d195f53c703cdd3ff45ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776941"
---
# <a name="importfile2-method"></a><span data-ttu-id="72215-102">ImportFile2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="72215-102">ImportFile2 Method</span></span>
<span data-ttu-id="72215-103">Importuje zestawy i niepowiązane moduły.</span><span class="sxs-lookup"><span data-stu-id="72215-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="72215-104">Ta metoda jest taka sama jak [Metoda ImportFile —](importfile-method.md), ale działa nawet wtedy, gdy importowany plik nie istnieje na dysku.</span><span class="sxs-lookup"><span data-stu-id="72215-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72215-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="72215-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="72215-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="72215-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="72215-107">Nazwa pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="72215-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="72215-108">Opcjonalna nazwa pliku wyjściowego, która może zostać użyta do zmiany nazwy pliku, ponieważ jest on połączony z zestawem.</span><span class="sxs-lookup"><span data-stu-id="72215-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="72215-109">Opcjonalny zakres interfejsu [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="72215-109">Optional scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="72215-110">Jeśli wartość jest równa TRUE, używane są wartości, w przeciwnym razie importowanie należy wykonać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="72215-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="72215-111">Odbiera identyfikator dla pliku lub zestawu.</span><span class="sxs-lookup"><span data-stu-id="72215-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="72215-112">Odbiera Interfejs [interfejsu IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="72215-112">Receives the [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="72215-113">Wartość NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="72215-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="72215-114">Odbiera znalezione pliki i/lub zakresy zaimportowane.</span><span class="sxs-lookup"><span data-stu-id="72215-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72215-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="72215-115">Return Value</span></span>  
 <span data-ttu-id="72215-116">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="72215-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72215-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72215-117">Requirements</span></span>  
 <span data-ttu-id="72215-118">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="72215-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72215-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72215-119">See also</span></span>

- [<span data-ttu-id="72215-120">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="72215-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="72215-121">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="72215-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="72215-122">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="72215-122">ALink API</span></span>](index.md)
