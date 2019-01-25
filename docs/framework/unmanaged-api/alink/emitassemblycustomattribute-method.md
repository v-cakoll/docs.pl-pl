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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b4909ae23d077ee079e062d0252dbf1ee11663c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538833"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="09848-102">EmitAssemblyCustomAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="09848-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="09848-103">Wywołać można ustawić na poziomie zestawu atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="09848-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09848-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09848-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="09848-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09848-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="09848-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="09848-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="09848-107">Plik, który defiles atrybutu.</span><span class="sxs-lookup"><span data-stu-id="09848-107">File that defiles the attribute.</span></span> <span data-ttu-id="09848-108">Może mieć wartości NULL, jeśli `AssemblyID` nie wskazuje niepowiązanych modułu netmodule.</span><span class="sxs-lookup"><span data-stu-id="09848-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="09848-109">Typ atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="09848-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="09848-110">Niestandardowa wartość danych.</span><span class="sxs-lookup"><span data-stu-id="09848-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="09848-111">Długość danych niestandardowych wartości.</span><span class="sxs-lookup"><span data-stu-id="09848-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="09848-112">Wartość TRUE, jeśli atrybut niestandardowy jest powiązany do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="09848-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="09848-113">Wartość TRUE, jeśli wiele atrybutów, które mają być emitowane.</span><span class="sxs-lookup"><span data-stu-id="09848-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09848-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="09848-114">Return Value</span></span>  
 <span data-ttu-id="09848-115">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="09848-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09848-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09848-116">Requirements</span></span>  
 <span data-ttu-id="09848-117">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="09848-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09848-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09848-118">See also</span></span>
- [<span data-ttu-id="09848-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="09848-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="09848-120">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="09848-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="09848-121">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="09848-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
