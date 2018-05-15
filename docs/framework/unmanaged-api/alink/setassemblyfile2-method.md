---
title: SetAssemblyFile2 — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ade568889d1c0203115f160d855de8c598798196
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="39d40-102">SetAssemblyFile2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="39d40-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="39d40-103">Ustawia opcje dla nowego zestawu i nazwa.</span><span class="sxs-lookup"><span data-stu-id="39d40-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="39d40-104">Ta metoda zostanie wywołana podczas tworzenia modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="39d40-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39d40-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="39d40-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39d40-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="39d40-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="39d40-107">Nazwa pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="39d40-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="39d40-108">[IMetaDataEmit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interfejs dla tego pliku.</span><span class="sxs-lookup"><span data-stu-id="39d40-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="39d40-109">Opcje reprezentowany przez [AssemblyFlags — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="39d40-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="39d40-110">Otrzymuje unikatowy identyfikator dla zestawu tworzona.</span><span class="sxs-lookup"><span data-stu-id="39d40-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39d40-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="39d40-111">Return Value</span></span>  
 <span data-ttu-id="39d40-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="39d40-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39d40-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39d40-113">Requirements</span></span>  
 <span data-ttu-id="39d40-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="39d40-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39d40-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39d40-115">See Also</span></span>  
 [<span data-ttu-id="39d40-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="39d40-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="39d40-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="39d40-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="39d40-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="39d40-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
