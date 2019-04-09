---
title: GetFileDef — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9153c9b3735e265d59ba072f747c92434c95d9ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184499"
---
# <a name="getfiledef-method"></a><span data-ttu-id="e04f8-102">GetFileDef — Metoda</span><span class="sxs-lookup"><span data-stu-id="e04f8-102">GetFileDef Method</span></span>
<span data-ttu-id="e04f8-103">Pobiera rzeczywisty token FileDef używana w metadanych (w przeciwieństwie do tokenu przypisany przez ALink).</span><span class="sxs-lookup"><span data-stu-id="e04f8-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e04f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e04f8-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e04f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e04f8-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e04f8-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="e04f8-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="e04f8-107">Token dodany plik uzyskana z metody AddFile lub addimport — metoda.</span><span class="sxs-lookup"><span data-stu-id="e04f8-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="e04f8-108">Odbiera FileDef token.</span><span class="sxs-lookup"><span data-stu-id="e04f8-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e04f8-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e04f8-109">Return Value</span></span>  
 <span data-ttu-id="e04f8-110">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="e04f8-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e04f8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e04f8-111">Requirements</span></span>  
 <span data-ttu-id="e04f8-112">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="e04f8-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e04f8-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e04f8-113">See also</span></span>

- [<span data-ttu-id="e04f8-114">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e04f8-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e04f8-115">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e04f8-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e04f8-116">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="e04f8-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
