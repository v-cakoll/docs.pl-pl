---
title: "Stałe (Niezarządzany wykaz interfejsów API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e086e856bb7a872b14815825f78d208ff5296899
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="259e7-102">Stałe (Niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="259e7-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="259e7-103">W tym temacie opisano typ języka dostawcy języka i stałe typu dokumentu, które są zdefiniowane w CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="259e7-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="259e7-104">Stałe typów języka</span><span class="sxs-lookup"><span data-stu-id="259e7-104">Language Type Constants</span></span>  
 <span data-ttu-id="259e7-105">W poniższej tabeli przedstawiono języka stałe typów, które reprezentują identyfikatorami GUID określającymi języków programowania.</span><span class="sxs-lookup"><span data-stu-id="259e7-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="259e7-106">Symbol</span><span class="sxs-lookup"><span data-stu-id="259e7-106">Symbol</span></span>|<span data-ttu-id="259e7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="259e7-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="259e7-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="259e7-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="259e7-109">Określa język C.</span><span class="sxs-lookup"><span data-stu-id="259e7-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="259e7-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="259e7-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="259e7-111">Wskazuje języka C++.</span><span class="sxs-lookup"><span data-stu-id="259e7-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="259e7-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="259e7-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="259e7-113">Wskazuje języka C#.</span><span class="sxs-lookup"><span data-stu-id="259e7-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="259e7-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="259e7-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="259e7-115">Wskazuje podstawowy język.</span><span class="sxs-lookup"><span data-stu-id="259e7-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="259e7-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="259e7-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="259e7-117">Wskazuje języka Java.</span><span class="sxs-lookup"><span data-stu-id="259e7-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="259e7-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="259e7-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="259e7-119">Określa język COBOL.</span><span class="sxs-lookup"><span data-stu-id="259e7-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="259e7-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="259e7-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="259e7-121">Określa język Pascal.</span><span class="sxs-lookup"><span data-stu-id="259e7-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="259e7-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="259e7-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="259e7-123">Wskazuje kod zestawu język pośredni (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="259e7-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="259e7-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="259e7-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="259e7-125">Wskazuje języka JScript.</span><span class="sxs-lookup"><span data-stu-id="259e7-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="259e7-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="259e7-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="259e7-127">Określa język SMC.</span><span class="sxs-lookup"><span data-stu-id="259e7-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="259e7-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="259e7-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="259e7-129">Określa język C++ włączone dla programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="259e7-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="259e7-130">Stałe dostawcy języka</span><span class="sxs-lookup"><span data-stu-id="259e7-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="259e7-131">W poniższej tabeli przedstawiono języka stałe dostawcy, które reprezentują identyfikatorami GUID określającymi dostawców języka programowania.</span><span class="sxs-lookup"><span data-stu-id="259e7-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="259e7-132">Symbol</span><span class="sxs-lookup"><span data-stu-id="259e7-132">Symbol</span></span>|<span data-ttu-id="259e7-133">Opis</span><span class="sxs-lookup"><span data-stu-id="259e7-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="259e7-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="259e7-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="259e7-135">Wskazuje firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="259e7-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="259e7-136">Stałe typu dokumentu</span><span class="sxs-lookup"><span data-stu-id="259e7-136">Document Type Constants</span></span>  
 <span data-ttu-id="259e7-137">W poniższej tabeli przedstawiono dokumentu stałe typów, które reprezentują identyfikatorami GUID określającymi typów dokumentów.</span><span class="sxs-lookup"><span data-stu-id="259e7-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="259e7-138">Symbol</span><span class="sxs-lookup"><span data-stu-id="259e7-138">Symbol</span></span>|<span data-ttu-id="259e7-139">Opis</span><span class="sxs-lookup"><span data-stu-id="259e7-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="259e7-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="259e7-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="259e7-141">Wskazuje dokument tekstowy.</span><span class="sxs-lookup"><span data-stu-id="259e7-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="259e7-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="259e7-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="259e7-143">Wskazuje nietekstowych dokumentu.</span><span class="sxs-lookup"><span data-stu-id="259e7-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="259e7-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="259e7-144">See Also</span></span>  
 [<span data-ttu-id="259e7-145">Niezarządzane interfejsy API — informacje</span><span class="sxs-lookup"><span data-stu-id="259e7-145">Unmanaged API Reference</span></span>](../../../docs/framework/unmanaged-api/index.md)
