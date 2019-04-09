---
title: SetManifestFile — Metoda
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8307960166cfc668a577431d688c439f0f794be2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072431"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="91558-102">SetManifestFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="91558-102">SetManifestFile Method</span></span>
<span data-ttu-id="91558-103">Pozwala na określenie lub zresetowania pliku manifestu, który konsolidator używa podczas tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="91558-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91558-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91558-104">Syntax</span></span>  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="91558-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91558-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="91558-106">Nazwa pliku manifestu, którego zawartość są umieszczane w obiekcie blob zasobów Win32.</span><span class="sxs-lookup"><span data-stu-id="91558-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91558-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="91558-107">Return Value</span></span>  
 <span data-ttu-id="91558-108">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="91558-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91558-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91558-109">Remarks</span></span>  
 <span data-ttu-id="91558-110">Połączenie się z tym przed żądaniem Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="91558-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="91558-111">Wartość `pszFile` parametr jest nazwą pliku manifestu, których zawartość jest odczytać i umieścić w zasoby Win32, za pomocą Identyfikatora RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="91558-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="91558-112">Gdy zostanie wywołana przy użyciu parametru o wartości NULL, jest wyczyszczone wszelkie wcześniej odczytu manifestu.</span><span class="sxs-lookup"><span data-stu-id="91558-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="91558-113">Dzięki temu jeden do zresetowania stanu konsolidator do tego czasu inicjowania.</span><span class="sxs-lookup"><span data-stu-id="91558-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91558-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91558-114">Requirements</span></span>  
 <span data-ttu-id="91558-115">Wymaga aLink.h</span><span class="sxs-lookup"><span data-stu-id="91558-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91558-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91558-116">See also</span></span>

- [<span data-ttu-id="91558-117">IALink3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="91558-117">IALink3 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)
- [<span data-ttu-id="91558-118">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="91558-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
- [<span data-ttu-id="91558-119">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="91558-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="91558-120">Al.exe (Konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="91558-120">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
