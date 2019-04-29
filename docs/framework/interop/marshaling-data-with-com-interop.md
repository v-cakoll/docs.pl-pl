---
title: Organizowanie danych za pomocą modelu COM
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab4dbdd0a69b158ff5c49949bee5089bd3fe095c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642938"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="7691f-102">Organizowanie danych za pomocą modelu COM</span><span class="sxs-lookup"><span data-stu-id="7691f-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="7691f-103">Usługa międzyoperacyjna modelu COM zapewnia obsługę zarówno za pomocą obiektów COM z kodu zarządzanego i udostępnianie zarządzane obiekty do modelu COM.</span><span class="sxs-lookup"><span data-stu-id="7691f-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="7691f-104">Obsługa kierowania danych do i z modelu COM są obszerne i prawie zawsze zawiera poprawne zachowanie organizowania.</span><span class="sxs-lookup"><span data-stu-id="7691f-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="7691f-105">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Obejmuje następujące narzędzia międzyoperacyjnego modelu COM:</span><span class="sxs-lookup"><span data-stu-id="7691f-105">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="7691f-106">[Importer biblioteki (Tlbimp.exe) wpisz](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), która konwertuje bibliotece typów modelu COM do zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7691f-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="7691f-107">Z tego zestawu międzyoperacyjnego marshaling usługi generuje otoki, które wykonują danych szeregowanie między zarządzanymi i niezarządzanymi pamięci.</span><span class="sxs-lookup"><span data-stu-id="7691f-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="7691f-108">[Eksporter biblioteki (Tlbexp.exe) wpisz](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), która generuje bibliotekę typów modelu COM z zestawu i generuje otoki, który wykonuje marshaling podczas wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="7691f-108">[Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="7691f-109">Poniższe sekcje łącza do tematów opisujących procesy dostosowywania otoki międzyoperacyjny podczas mogą lub musi podawania organizator informacji o dodatkowych typach.</span><span class="sxs-lookup"><span data-stu-id="7691f-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7691f-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7691f-110">In This Section</span></span>  
<span data-ttu-id="7691f-111">[Instrukcje: Ręczne tworzenie otok](how-to-create-wrappers-manually.md) </span><span class="sxs-lookup"><span data-stu-id="7691f-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) </span></span>  
<span data-ttu-id="7691f-112">W tym artykule opisano sposób tworzenia otoki COM ręcznie w zarządzanym kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="7691f-112">Describes how to create a COM wrapper manually in managed source code.</span></span> 
 
 [<span data-ttu-id="7691f-113">Instrukcje: Migrowanie zarządzanego kodu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="7691f-113">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="7691f-114">W tym artykule opisano, jak przeprowadzić migrację zarządzanego kodu DCOM do WCF dla najbardziej bezpieczne rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="7691f-114">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7691f-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7691f-115">Related Sections</span></span>  
 <span data-ttu-id="7691f-116">[Typy danych COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7691f-116">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="7691f-117">Udostępnia odpowiednie typy danych zarządzanych i niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="7691f-117">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="7691f-118">[Dostosowywanie wywoływanych otok COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7691f-118">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="7691f-119">Opisuje sposób kieruje jawnie tego typów danych przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="7691f-119">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="7691f-120">[Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7691f-120">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="7691f-121">W tym artykule opisano, jak dostosować zachowanie organizowania typów w zestaw międzyoperacyjny oraz sposób definiowania typów modelu COM ręcznie.</span><span class="sxs-lookup"><span data-stu-id="7691f-121">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="7691f-122">[Zaawansowane współdziałanie modeli COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7691f-122">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="7691f-123">Zawiera łącza do dodatkowych informacji o dołączaniu składników COM do aplikacji środowiska .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7691f-123">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="7691f-124">[Zestaw do wpisz biblioteki konwersja — podsumowanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7691f-124">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="7691f-125">W tym artykule opisano zestaw na typ procesu konwersji eksportu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="7691f-125">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="7691f-126">[Biblioteki typów na zestaw konwersja — podsumowanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7691f-126">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="7691f-127">W tym artykule opisano biblioteki typów do procesu konwersji importowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="7691f-127">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="7691f-128">[Międzyoperacyjne używanie typów ogólnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7691f-128">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="7691f-129">W tym artykule opisano akcje, które są obsługiwane w przypadku współdziałania COM za pomocą typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="7691f-129">Describes which actions are supported when using generic types for COM interoperability.</span></span>
