---
title: SetAssemblyFile — Metoda
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76d341aca7c96e5932a1fc155ccaee17ce6585da
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777005"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="11965-102">SetAssemblyFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="11965-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="11965-103">Przypisuje nazwę zestawu, który ma zostać skompilowany.</span><span class="sxs-lookup"><span data-stu-id="11965-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="11965-104">Nie do użycia podczas tworzenia niezwiązanych modułów.</span><span class="sxs-lookup"><span data-stu-id="11965-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11965-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="11965-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="11965-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="11965-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="11965-107">W pełni kwalifikowana nazwa pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="11965-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="11965-108">Wskaźnik do interfejsu [interfejsu IMetaDataEmit](../metadata/imetadataemit-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="11965-108">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="11965-109">Flagi zgodnie z definicją w [wyliczeniu AssemblyFlags —](../metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="11965-109">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="11965-110">Wskaźnik na identyfikator tworzonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="11965-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11965-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="11965-111">Return Value</span></span>  
 <span data-ttu-id="11965-112">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="11965-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11965-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11965-113">Requirements</span></span>  
 <span data-ttu-id="11965-114">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="11965-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11965-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11965-115">See also</span></span>

- [<span data-ttu-id="11965-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="11965-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="11965-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="11965-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="11965-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="11965-118">ALink API</span></span>](index.md)
