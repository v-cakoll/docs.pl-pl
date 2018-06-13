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
ms.openlocfilehash: f40b99c0a81bf0f2b622c7d23157dbb5736df1ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403295"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="5411e-102">GetWin32ResBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="5411e-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="5411e-103">Pobiera obiekt blob zasobów Win32.</span><span class="sxs-lookup"><span data-stu-id="5411e-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="5411e-104">Tę metodę można wywołać po ustawieniu opcji zestawu.</span><span class="sxs-lookup"><span data-stu-id="5411e-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5411e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5411e-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="5411e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5411e-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="5411e-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="5411e-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="5411e-108">Token pliku używany do pobierania nazwy pliku do użycia podczas tworzenia zasobów Win32 wersji</span><span class="sxs-lookup"><span data-stu-id="5411e-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="5411e-109">Wartość TRUE, jeśli plik jest biblioteki DLL, false dla pliku EXE.</span><span class="sxs-lookup"><span data-stu-id="5411e-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="5411e-110">Ikona opcjonalne wstawiania do obiektu blob zasobów.</span><span class="sxs-lookup"><span data-stu-id="5411e-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="5411e-111">Odbiera zasobów obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="5411e-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="5411e-112">Odbiera rozmiar obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="5411e-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5411e-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5411e-113">Return Value</span></span>  
 <span data-ttu-id="5411e-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5411e-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5411e-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5411e-115">Requirements</span></span>  
 <span data-ttu-id="5411e-116">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="5411e-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5411e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5411e-117">See Also</span></span>  
 [<span data-ttu-id="5411e-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="5411e-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="5411e-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5411e-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="5411e-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="5411e-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
