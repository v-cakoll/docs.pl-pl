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
ms.openlocfilehash: f7fee7a91de99e2db69609cbc7c73e22d85d045f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777063"
---
# <a name="importfile-method"></a><span data-ttu-id="5f7e3-102">ImportFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="5f7e3-102">ImportFile Method</span></span>
<span data-ttu-id="5f7e3-103">Importuje zestawy i niepowiązane moduły.</span><span class="sxs-lookup"><span data-stu-id="5f7e3-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f7e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f7e3-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f7e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f7e3-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="5f7e3-106">W pełni kwalifikowana nazwa pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="5f7e3-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="5f7e3-107">Opcjonalna nazwa pliku wyjściowego, która może zostać użyta do zmiany nazwy pliku, ponieważ jest on połączony z zestawem.</span><span class="sxs-lookup"><span data-stu-id="5f7e3-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="5f7e3-108">Jeśli wartość jest równa TRUE, używane są wartości, w przeciwnym razie importowanie należy wykonać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="5f7e3-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="5f7e3-109">Wskaźnik do tokenu, w którym będzie przechowywany unikatowy identyfikator pliku.</span><span class="sxs-lookup"><span data-stu-id="5f7e3-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="5f7e3-110">Plik może być zestawem lub plikiem.</span><span class="sxs-lookup"><span data-stu-id="5f7e3-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="5f7e3-111">Odbiera wskaźnik do [interfejsu IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5f7e3-111">Receives pointer to [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="5f7e3-112">Może mieć wartość NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="5f7e3-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="5f7e3-113">Wskaźnik do liczby zaimportowanych plików i/lub zakresów.</span><span class="sxs-lookup"><span data-stu-id="5f7e3-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f7e3-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5f7e3-114">Return Value</span></span>  
 <span data-ttu-id="5f7e3-115">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5f7e3-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f7e3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f7e3-116">Requirements</span></span>  
 <span data-ttu-id="5f7e3-117">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="5f7e3-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f7e3-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f7e3-118">See also</span></span>

- [<span data-ttu-id="5f7e3-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f7e3-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5f7e3-120">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f7e3-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5f7e3-121">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="5f7e3-121">ALink API</span></span>](index.md)
