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
ms.openlocfilehash: 3882998d3155b49251fbe091b72ef11022ebfd2b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540211"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="75ba0-102">SetAssemblyFile2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="75ba0-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="75ba0-103">Określa nazwę i opcje dla nowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="75ba0-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="75ba0-104">Ta metoda zostanie wywołana podczas tworzenia modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="75ba0-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75ba0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="75ba0-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75ba0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="75ba0-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="75ba0-107">Nazwa pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="75ba0-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="75ba0-108">[Imetadataemit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interfejsu dla tego pliku.</span><span class="sxs-lookup"><span data-stu-id="75ba0-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="75ba0-109">Opcje reprezentowany przez [assemblyflags — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="75ba0-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="75ba0-110">Otrzymuje unikatowy identyfikator dla zestawu podczas konstruowania.</span><span class="sxs-lookup"><span data-stu-id="75ba0-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75ba0-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="75ba0-111">Return Value</span></span>  
 <span data-ttu-id="75ba0-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="75ba0-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75ba0-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75ba0-113">Requirements</span></span>  
 <span data-ttu-id="75ba0-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="75ba0-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75ba0-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75ba0-115">See also</span></span>
- [<span data-ttu-id="75ba0-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="75ba0-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="75ba0-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="75ba0-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="75ba0-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="75ba0-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
