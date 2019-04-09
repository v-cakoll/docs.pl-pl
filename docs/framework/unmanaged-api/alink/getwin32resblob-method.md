---
title: GetWin32ResBlob — Metoda
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4c77ade46d2401e2499a94504808efd94f79f93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152155"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="f5a8a-102">GetWin32ResBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="f5a8a-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="f5a8a-103">Pobiera obiekt blob zasobów Win32.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="f5a8a-104">Wywołaj tę metodę po ustawieniu opcji zestawu.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5a8a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5a8a-105">Syntax</span></span>  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5a8a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5a8a-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f5a8a-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f5a8a-108">Token pliku używany do pobrania nazwy pliku, który będzie używany podczas tworzenia zasobów Win32 w wersji</span><span class="sxs-lookup"><span data-stu-id="f5a8a-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="f5a8a-109">Wartość TRUE, jeśli plik jest biblioteką DLL, false dla pliku EXE.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="f5a8a-110">Opcjonalne ikona Wstawianie obiektu blob zasobów.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="f5a8a-111">Odbiera zasobów obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="f5a8a-112">Uzyskuje rozmiar obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5a8a-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f5a8a-113">Return Value</span></span>  
 <span data-ttu-id="f5a8a-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f5a8a-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5a8a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5a8a-115">Requirements</span></span>  
 <span data-ttu-id="f5a8a-116">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="f5a8a-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5a8a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5a8a-117">See also</span></span>

- [<span data-ttu-id="f5a8a-118">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f5a8a-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f5a8a-119">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f5a8a-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f5a8a-120">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="f5a8a-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
