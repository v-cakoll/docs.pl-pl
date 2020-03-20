---
title: Organizowanie danych za pomocą modelu COM
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: ae41713d5349321725599c0c38d7c6fc515c374b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181371"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="9bdf5-102">Organizowanie danych za pomocą modelu COM</span><span class="sxs-lookup"><span data-stu-id="9bdf5-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="9bdf5-103">Współdziałanie COM zapewnia obsługę zarówno przy użyciu obiektów COM z kodu zarządzanego, jak i uwidaczniania zarządzanych obiektów na platformie COM.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="9bdf5-104">Obsługa organizowania danych do i z COM jest obszerna i prawie zawsze zapewnia prawidłowe zachowanie organizowania.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="9bdf5-105">Zestaw Windows SDK zawiera następujące narzędzia międzyoperacyjne COM:</span><span class="sxs-lookup"><span data-stu-id="9bdf5-105">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="9bdf5-106">[Importer biblioteki typów (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), który konwertuje bibliotekę typów COM na zestaw międzyoperacyjny.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-106">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="9bdf5-107">Z tego zestawu międzyoperacyjnej usługi organizowania generuje otoki, które wykonują rozrządzania danych między pamięcią zarządzaną i niezarządzaną.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="9bdf5-108">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), który tworzy bibliotekę typów COM z zestawu i generuje otokę, która wykonuje kierowanie podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-108">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="9bdf5-109">W poniższych sekcjach łącze do tematów, które opisują procesy dostosowywania otoki międzyop, gdy można (lub musi) dostarczyć organizatora dodatkowe informacje o typie.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9bdf5-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9bdf5-110">In This Section</span></span>  
<span data-ttu-id="9bdf5-111">[Jak: Ręczne tworzenie otoków](how-to-create-wrappers-manually.md) W tym artykule opisano sposób ręcznego tworzenia otoki COM w zarządzanym kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="9bdf5-112">Instrukcje: migrowanie zarządzanego kodu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="9bdf5-112">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="9bdf5-113">W tym artykule opisano sposób migracji zarządzanego kodu DCOM do WCF dla najbardziej bezpiecznego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-113">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9bdf5-114">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9bdf5-114">Related Sections</span></span>  
 <span data-ttu-id="9bdf5-115">[Typy danych COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9bdf5-115">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="9bdf5-116">Zawiera odpowiednie typy danych zarządzanych i niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-116">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="9bdf5-117">[Dostosowywanie otoki współusznezwalne COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9bdf5-117">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="9bdf5-118">W tym artykule opisano, <xref:System.Runtime.InteropServices.MarshalAsAttribute> jak jawnie marshal typy danych przy użyciu atrybutu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-118">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="9bdf5-119">[Dostosowywanie otoki wywoławcze w czasie wykonywania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9bdf5-119">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="9bdf5-120">W tym artykule opisano, jak dostosować zachowanie organizowania typów w zestawie międzyoperacyjnym i jak zdefiniować typy COM ręcznie.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-120">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="9bdf5-121">[Zaawansowana interoperacyjność COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9bdf5-121">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="9bdf5-122">Zawiera łącza do więcej informacji na temat dołączania składników COM do aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-122">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="9bdf5-123">[Podsumowanie konwersji biblioteki zdań do biblioteki typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9bdf5-123">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="9bdf5-124">Opisuje zestaw do wpisywania procesu konwersji eksportu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-124">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="9bdf5-125">[Podsumowanie konwersji biblioteki typów na podsumowanie konwersji zestawu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9bdf5-125">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="9bdf5-126">Zawiera opis biblioteki typów do procesu konwersji importu zestawu.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-126">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="9bdf5-127">[Współdziałanie przy użyciu typów ogólnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9bdf5-127">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="9bdf5-128">W tym artykule opisano, które akcje są obsługiwane podczas korzystania z typów ogólnych dla współdziałania COM.</span><span class="sxs-lookup"><span data-stu-id="9bdf5-128">Describes which actions are supported when using generic types for COM interoperability.</span></span>
