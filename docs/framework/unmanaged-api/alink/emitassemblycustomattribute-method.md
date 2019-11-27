---
title: EmitAssemblyCustomAttribute — Metoda
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
ms.openlocfilehash: ec0a86e3396ad42152bc0a244f74ad13deba16e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446508"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="3c344-102">EmitAssemblyCustomAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="3c344-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="3c344-103">Wywołanie ustawiania atrybutów niestandardowych na poziomie zestawu.</span><span class="sxs-lookup"><span data-stu-id="3c344-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c344-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c344-104">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c344-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c344-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3c344-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="3c344-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3c344-107">Plik, który deplikuje atrybut.</span><span class="sxs-lookup"><span data-stu-id="3c344-107">File that defiles the attribute.</span></span> <span data-ttu-id="3c344-108">Może mieć wartość NULL, jeśli `AssemblyID` nie wskazuje niepowiązanego modułu.</span><span class="sxs-lookup"><span data-stu-id="3c344-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="3c344-109">Typ atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="3c344-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="3c344-110">Dane wartości niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="3c344-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="3c344-111">Długość danych wartości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="3c344-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="3c344-112">Ma wartość TRUE, jeśli atrybut niestandardowy jest powiązany z podpisywaniem zestawu.</span><span class="sxs-lookup"><span data-stu-id="3c344-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="3c344-113">Ma wartość TRUE, jeśli wiele atrybutów ma być emitowanych.</span><span class="sxs-lookup"><span data-stu-id="3c344-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c344-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3c344-114">Return Value</span></span>  
 <span data-ttu-id="3c344-115">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3c344-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c344-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c344-116">Requirements</span></span>  
 <span data-ttu-id="3c344-117">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="3c344-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c344-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c344-118">See also</span></span>

- [<span data-ttu-id="3c344-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c344-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3c344-120">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c344-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3c344-121">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="3c344-121">ALink API</span></span>](index.md)
