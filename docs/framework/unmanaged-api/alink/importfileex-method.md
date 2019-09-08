---
title: ImportFileEx — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd138d0418bb9667a86419d719bf0b95a4bb1b12
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777112"
---
# <a name="importfileex-method"></a><span data-ttu-id="8f701-102">ImportFileEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="8f701-102">ImportFileEx Method</span></span>
<span data-ttu-id="8f701-103">Importuje wskazany zestaw lub niezwiązany moduł.</span><span class="sxs-lookup"><span data-stu-id="8f701-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f701-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f701-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f701-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f701-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="8f701-106">W pełni kwalifikowana nazwa pliku, z którego ma zostać zaimportowana.</span><span class="sxs-lookup"><span data-stu-id="8f701-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="8f701-107">Opcjonalna nazwa pliku docelowego.</span><span class="sxs-lookup"><span data-stu-id="8f701-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="8f701-108">Jeśli wartość jest równa TRUE, używane są wartości, w przeciwnym razie importowanie należy wykonać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="8f701-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="8f701-109">Flagi do przesłania do [metody OpenScope —](../metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="8f701-109">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="8f701-110">Odbiera identyfikator importowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="8f701-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="8f701-111">Odbiera Interfejs [IMetaDataAssemblyImporty](../metadata/imetadataassemblyimport-interface.md) zakresu importu zestawu.</span><span class="sxs-lookup"><span data-stu-id="8f701-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="8f701-112">Jest ustawiona na wartość NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="8f701-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="8f701-113">Odbiera liczbę zaimportowanych plików i/lub zakresów.</span><span class="sxs-lookup"><span data-stu-id="8f701-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f701-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8f701-114">Return Value</span></span>  
 <span data-ttu-id="8f701-115">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8f701-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f701-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f701-116">Requirements</span></span>  
 <span data-ttu-id="8f701-117">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="8f701-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f701-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f701-118">See also</span></span>

- [<span data-ttu-id="8f701-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f701-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8f701-120">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f701-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8f701-121">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="8f701-121">ALink API</span></span>](index.md)
