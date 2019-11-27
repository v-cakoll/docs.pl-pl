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
ms.openlocfilehash: 1db4c4ab7e47e223a492e08297ac3cedcb3a27eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445608"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="6edda-102">SetAssemblyFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="6edda-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="6edda-103">Przypisuje nazwę zestawu, który ma zostać skompilowany.</span><span class="sxs-lookup"><span data-stu-id="6edda-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="6edda-104">Nie do użycia podczas tworzenia niezwiązanych modułów.</span><span class="sxs-lookup"><span data-stu-id="6edda-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6edda-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6edda-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6edda-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6edda-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="6edda-107">W pełni kwalifikowana nazwa pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="6edda-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="6edda-108">Wskaźnik do interfejsu [interfejsu IMetaDataEmit](../metadata/imetadataemit-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6edda-108">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="6edda-109">Flagi zgodnie z definicją w [wyliczeniu AssemblyFlags —](../metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="6edda-109">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="6edda-110">Wskaźnik na identyfikator tworzonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="6edda-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6edda-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6edda-111">Return Value</span></span>  
 <span data-ttu-id="6edda-112">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6edda-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6edda-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6edda-113">Requirements</span></span>  
 <span data-ttu-id="6edda-114">Wymaga Alink. h.</span><span class="sxs-lookup"><span data-stu-id="6edda-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6edda-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6edda-115">See also</span></span>

- [<span data-ttu-id="6edda-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="6edda-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6edda-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6edda-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6edda-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="6edda-118">ALink API</span></span>](index.md)
