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
ms.openlocfilehash: 807452326193d193f3bc603ebc7b74a5a0f1c281
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="7a033-102">SetManifestFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="7a033-102">SetManifestFile Method</span></span>
<span data-ttu-id="7a033-103">Pozwala określić lub zresetować plik manifestu podczas tworzenia zestawu używa konsolidator.</span><span class="sxs-lookup"><span data-stu-id="7a033-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a033-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a033-104">Syntax</span></span>  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a033-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a033-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="7a033-106">Nazwa pliku manifestu, których zawartość są umieszczane w obiekcie blob zasobów Win32.</span><span class="sxs-lookup"><span data-stu-id="7a033-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a033-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7a033-107">Return Value</span></span>  
 <span data-ttu-id="7a033-108">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="7a033-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a033-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a033-109">Remarks</span></span>  
 <span data-ttu-id="7a033-110">Wywołaj ten element przed żądaniem Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="7a033-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="7a033-111">Wartość `pszFile` parametr jest nazwą pliku manifestu, których zawartość jest do odczytu i umieść w zasobów Win32 o identyfikatorze RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="7a033-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="7a033-112">Po wywołaniu za pomocą parametru o wartości NULL, wszystkie wcześniej odczytu manifestu jest wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="7a033-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="7a033-113">Dzięki temu jeden do zresetowania stanu konsolidator niż czas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="7a033-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a033-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a033-114">Requirements</span></span>  
 <span data-ttu-id="7a033-115">Wymaga aLink.h</span><span class="sxs-lookup"><span data-stu-id="7a033-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a033-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a033-116">See Also</span></span>  
 [<span data-ttu-id="7a033-117">Ialink3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="7a033-117">IALink3 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [<span data-ttu-id="7a033-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="7a033-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [<span data-ttu-id="7a033-119">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="7a033-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7a033-120">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="7a033-120">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
