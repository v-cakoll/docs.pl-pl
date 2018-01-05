---
title: "Marshaling danych za pomocą modelu COM"
ms.custom: 
ms.date: 09/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2af80ddb558959171c255a61fae460729306e0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="d311f-102">Marshaling danych za pomocą modelu COM</span><span class="sxs-lookup"><span data-stu-id="d311f-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="d311f-103">Współdziałanie z COM zapewnia obsługę zarówno przy użyciu obiektów COM z kodu zarządzanego i udostępnianie zarządzane obiekty do modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d311f-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="d311f-104">Obsługa przekazywanie danych do i z modelu COM jest rozbudowana i prawie zawsze zawiera poprawne zachowanie marshalingu.</span><span class="sxs-lookup"><span data-stu-id="d311f-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="d311f-105">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Obejmuje następujące narzędzia międzyoperacyjnego COM:</span><span class="sxs-lookup"><span data-stu-id="d311f-105">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] includes the following COM interop tools:</span></span>  
  
-   <span data-ttu-id="d311f-106">[Importer biblioteki (Tlbimp.exe) wpisz](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), który konwertuje Biblioteka typów COM do zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d311f-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="d311f-107">Z tego zestawu interop organizowanie usługi generuje otoki wykonujących przekazywanie między zarządzanymi i niezarządzanymi pamięci danych.</span><span class="sxs-lookup"><span data-stu-id="d311f-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
-   <span data-ttu-id="d311f-108">[Eksporter biblioteki (Tlbexp.exe) wpisz](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), która tworzy bibliotekę typów COM z zestawu i generuje otoki, który wykonuje przekazywanie podczas wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="d311f-108">[Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="d311f-109">Poniższe sekcje łącza do tematów opisujących procesów dostosowywania otoki międzyoperacyjnego, jeśli można lub musi podasz organizatora typu dodatkowe informacje.</span><span class="sxs-lookup"><span data-stu-id="d311f-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d311f-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d311f-110">In This Section</span></span>  
<span data-ttu-id="d311f-111">[Porady: ręczne tworzenie otok](how-to-create-wrappers-manually.md) </span><span class="sxs-lookup"><span data-stu-id="d311f-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) </span></span>  
<span data-ttu-id="d311f-112">Opisuje sposób tworzenia otoki COM ręcznie w kodzie źródłowym zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="d311f-112">Describes how to create a COM wrapper manually in managed source code.</span></span> 
 
 [<span data-ttu-id="d311f-113">Instrukcje: Migrowanie zarządzanego kodu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="d311f-113">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="d311f-114">Opisuje sposób Migrowanie zarządzanego kodu DCOM do WCF dla najbardziej bezpieczne rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d311f-114">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d311f-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d311f-115">Related Sections</span></span>  
 <span data-ttu-id="d311f-116">[Typy danych modelu COM](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="d311f-116">[COM Data Types](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="d311f-117">Zawiera odpowiednie typy zarządzane i niezarządzane danych.</span><span class="sxs-lookup"><span data-stu-id="d311f-117">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="d311f-118">[Dostosowywanie wywoływane otoki COM](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="d311f-118">[Customizing COM Callable Wrappers](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="d311f-119">Opisuje sposób jawnie kierować typy danych przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="d311f-119">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="d311f-120">[Dostosowywanie wywoływane otoki środowiska uruchomieniowego](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="d311f-120">[Customizing Runtime Callable Wrappers](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="d311f-121">Opisuje sposób dostosować zachowanie marshalingu typów z zestawu międzyoperacyjnego oraz definiowanie typów COM ręcznie.</span><span class="sxs-lookup"><span data-stu-id="d311f-121">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="d311f-122">[Współdziałanie COM zaawansowane](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="d311f-122">[Advanced COM Interoperability](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="d311f-123">Zawiera łącza do dodatkowych informacji o włączenie składniki modelu COM aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d311f-123">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="d311f-124">[Zestaw do typu biblioteki konwersja — podsumowanie](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="d311f-124">[Assembly to Type Library Conversion Summary](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="d311f-125">Zawiera opis zestawu na typ procesu konwersji eksportu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d311f-125">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="d311f-126">[Biblioteki typów na zestaw konwersja — podsumowanie](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="d311f-126">[Type Library to Assembly Conversion Summary](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="d311f-127">W tym artykule opisano bibliotekę typów, aby proces konwersji importu zestawu.</span><span class="sxs-lookup"><span data-stu-id="d311f-127">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="d311f-128">[Współdziałanie za pomocą typów ogólnych](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="d311f-128">[Interoperating Using Generic Types](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="d311f-129">Opisuje akcje, które są obsługiwane w przypadku współdziałania COM za pomocą typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="d311f-129">Describes which actions are supported when using generic types for COM interoperability.</span></span>
