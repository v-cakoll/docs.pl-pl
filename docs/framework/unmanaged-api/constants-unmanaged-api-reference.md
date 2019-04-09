---
title: Stałe (Niezarządzany wykaz interfejsów API)
ms.date: 03/30/2017
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c76db644ffee478003d834460c155c4ec6d0070
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133955"
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="0563c-102">Stałe (Niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="0563c-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="0563c-103">W tym temacie opisano typ języka, dostawcy języka i stałe typów dokumentów, które są zdefiniowane w CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="0563c-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="0563c-104">Stałe typów języka</span><span class="sxs-lookup"><span data-stu-id="0563c-104">Language Type Constants</span></span>  
 <span data-ttu-id="0563c-105">W poniższej tabeli przedstawiono języka stałe typów, które reprezentują identyfikatorami GUID określającymi języków programowania.</span><span class="sxs-lookup"><span data-stu-id="0563c-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="0563c-106">Symbol</span><span class="sxs-lookup"><span data-stu-id="0563c-106">Symbol</span></span>|<span data-ttu-id="0563c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0563c-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0563c-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="0563c-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="0563c-109">Określa język C.</span><span class="sxs-lookup"><span data-stu-id="0563c-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="0563c-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="0563c-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="0563c-111">Wskazuje języka C++.</span><span class="sxs-lookup"><span data-stu-id="0563c-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="0563c-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="0563c-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="0563c-113">Wskazuje C# języka.</span><span class="sxs-lookup"><span data-stu-id="0563c-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="0563c-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="0563c-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="0563c-115">Wskazuje podstawowy język.</span><span class="sxs-lookup"><span data-stu-id="0563c-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="0563c-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="0563c-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="0563c-117">Wskazuje języka Java.</span><span class="sxs-lookup"><span data-stu-id="0563c-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="0563c-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="0563c-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="0563c-119">Określa język COBOL.</span><span class="sxs-lookup"><span data-stu-id="0563c-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="0563c-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="0563c-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="0563c-121">Określa język Pascal.</span><span class="sxs-lookup"><span data-stu-id="0563c-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="0563c-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="0563c-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="0563c-123">Wskazuje kod zestawu Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="0563c-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="0563c-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="0563c-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="0563c-125">Wskazuje języka JScript.</span><span class="sxs-lookup"><span data-stu-id="0563c-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="0563c-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="0563c-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="0563c-127">Określa język SMC.</span><span class="sxs-lookup"><span data-stu-id="0563c-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="0563c-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="0563c-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="0563c-129">Wskazuje języka C++, włączone dla programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0563c-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="0563c-130">Stałe dostawcy języka</span><span class="sxs-lookup"><span data-stu-id="0563c-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="0563c-131">W poniższej tabeli przedstawiono języka dostawcy stałych, które reprezentują identyfikatorami GUID określającymi programowania dostawców języka.</span><span class="sxs-lookup"><span data-stu-id="0563c-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="0563c-132">Symbol</span><span class="sxs-lookup"><span data-stu-id="0563c-132">Symbol</span></span>|<span data-ttu-id="0563c-133">Opis</span><span class="sxs-lookup"><span data-stu-id="0563c-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0563c-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="0563c-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="0563c-135">Wskazuje firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0563c-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="0563c-136">Stałe typów dokumentów</span><span class="sxs-lookup"><span data-stu-id="0563c-136">Document Type Constants</span></span>  
 <span data-ttu-id="0563c-137">W poniższej tabeli przedstawiono dokumentu stałe typów, które reprezentują identyfikatorami GUID określającymi typy dokumentów.</span><span class="sxs-lookup"><span data-stu-id="0563c-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="0563c-138">Symbol</span><span class="sxs-lookup"><span data-stu-id="0563c-138">Symbol</span></span>|<span data-ttu-id="0563c-139">Opis</span><span class="sxs-lookup"><span data-stu-id="0563c-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0563c-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="0563c-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="0563c-141">Wskazuje dokument tekstowy.</span><span class="sxs-lookup"><span data-stu-id="0563c-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="0563c-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="0563c-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="0563c-143">Wskazuje dokument-text.</span><span class="sxs-lookup"><span data-stu-id="0563c-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0563c-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0563c-144">See also</span></span>

- [<span data-ttu-id="0563c-145">Niezarządzany wykaz interfejsów API</span><span class="sxs-lookup"><span data-stu-id="0563c-145">Unmanaged API Reference</span></span>](../../../docs/framework/unmanaged-api/index.md)
