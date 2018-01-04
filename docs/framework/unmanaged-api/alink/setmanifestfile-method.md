---
title: "SetManifestFile — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink3.SetManifestFile
api_location: alink.dll
api_type: COM
f1_keywords: SetManifestFile
helpviewer_keywords: SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf48153454fbb2c24dc3f1cfe1f82deefa4ee723
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="12cac-102">SetManifestFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="12cac-102">SetManifestFile Method</span></span>
<span data-ttu-id="12cac-103">Pozwala określić lub zresetować plik manifestu podczas tworzenia zestawu używa konsolidator.</span><span class="sxs-lookup"><span data-stu-id="12cac-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12cac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="12cac-104">Syntax</span></span>  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12cac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12cac-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="12cac-106">Nazwa pliku manifestu, których zawartość są umieszczane w obiekcie blob zasobów Win32.</span><span class="sxs-lookup"><span data-stu-id="12cac-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12cac-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="12cac-107">Return Value</span></span>  
 <span data-ttu-id="12cac-108">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="12cac-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12cac-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12cac-109">Remarks</span></span>  
 <span data-ttu-id="12cac-110">Wywołaj ten element przed żądaniem Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="12cac-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="12cac-111">Wartość `pszFile` parametr jest nazwą pliku manifestu, których zawartość jest do odczytu i umieść w zasobów Win32 o identyfikatorze RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="12cac-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="12cac-112">Po wywołaniu za pomocą parametru o wartości NULL, wszystkie wcześniej odczytu manifestu jest wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="12cac-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="12cac-113">Dzięki temu jeden do zresetowania stanu konsolidator niż czas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="12cac-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12cac-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12cac-114">Requirements</span></span>  
 <span data-ttu-id="12cac-115">Wymaga aLink.h</span><span class="sxs-lookup"><span data-stu-id="12cac-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12cac-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12cac-116">See Also</span></span>  
 [<span data-ttu-id="12cac-117">IALink3, interfejs</span><span class="sxs-lookup"><span data-stu-id="12cac-117">IALink3 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [<span data-ttu-id="12cac-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="12cac-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [<span data-ttu-id="12cac-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="12cac-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="12cac-120">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="12cac-120">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
