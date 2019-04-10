---
title: GetPublicKeyToken — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d1b28eadc9f09abff799f99d1d6012c98b1d3dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215771"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="dacac-102">GetPublicKeyToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="dacac-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="dacac-103">Pobiera token klucza publicznego do pliku danego klucza lub kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="dacac-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dacac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dacac-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="dacac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dacac-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="dacac-106">Nazwa pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="dacac-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="dacac-107">Nazwa kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="dacac-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="dacac-108">Adres, gdzie token klucza ma być przechowywany.</span><span class="sxs-lookup"><span data-stu-id="dacac-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="dacac-109">Określa rozmiar w bajtach, bufor wskazywany przez `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="dacac-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="dacac-110">Po powrocie zawiera rzeczywista liczba bajtów używanych.</span><span class="sxs-lookup"><span data-stu-id="dacac-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dacac-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dacac-111">Return Value</span></span>  
 <span data-ttu-id="dacac-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="dacac-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dacac-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dacac-113">Requirements</span></span>  
 <span data-ttu-id="dacac-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="dacac-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dacac-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dacac-115">See also</span></span>

- [<span data-ttu-id="dacac-116">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dacac-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="dacac-117">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dacac-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="dacac-118">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="dacac-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
