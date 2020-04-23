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
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="d1f74-102">Organizowanie danych za pomocą modelu COM</span><span class="sxs-lookup"><span data-stu-id="d1f74-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="d1f74-103">Współdziałanie modelu COM zapewnia obsługę zarówno obiektów COM z kodu zarządzanego, jak i Uwidacznianie obiektów zarządzanych w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d1f74-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="d1f74-104">Obsługa przekazywania danych do i z modelu COM jest obszerna i prawie zawsze zapewnia prawidłowe zachowanie organizowania.</span><span class="sxs-lookup"><span data-stu-id="d1f74-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="d1f74-105">Windows SDK obejmuje następujące narzędzia międzyoperacyjności modelu COM:</span><span class="sxs-lookup"><span data-stu-id="d1f74-105">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="d1f74-106">[Importer biblioteki typów (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md), który konwertuje bibliotekę typów com na zestaw międzyoperacyjny.</span><span class="sxs-lookup"><span data-stu-id="d1f74-106">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="d1f74-107">Z tego zestawu usługa Marshaling Interop generuje otoki, które wykonują kierowanie danych między zarządzaną i niezarządzaną pamięcią.</span><span class="sxs-lookup"><span data-stu-id="d1f74-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="d1f74-108">[Eksporter biblioteki typów (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md), który tworzy bibliotekę typów com z zestawu i generuje otokę wykonującą operacje organizowania podczas wywołań metod.</span><span class="sxs-lookup"><span data-stu-id="d1f74-108">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="d1f74-109">W poniższych sekcjach znajdują się łącza do tematów opisujących procesy dostosowywania otok międzyoperacyjnych, gdy użytkownik może (lub musi) dostarczyć Organizatorowi dodatkowe informacje o typie.</span><span class="sxs-lookup"><span data-stu-id="d1f74-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1f74-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d1f74-110">In This Section</span></span>  
<span data-ttu-id="d1f74-111">[Instrukcje: ręczne tworzenie otok](how-to-create-wrappers-manually.md) Opisuje sposób ręcznego tworzenia otoki COM w zarządzanym kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="d1f74-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="d1f74-112">Instrukcje: migrowanie zarządzanego kodu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="d1f74-112">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="d1f74-113">Opisuje sposób migrowania zarządzanego kodu DCOM do usługi WCF w celu zapewnienia najbezpieczniejszego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d1f74-113">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d1f74-114">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d1f74-114">Related Sections</span></span>  
 <span data-ttu-id="d1f74-115">[Typy danych COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d1f74-115">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="d1f74-116">Zapewnia odpowiednie zarządzane i niezarządzane typy danych.</span><span class="sxs-lookup"><span data-stu-id="d1f74-116">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="d1f74-117">[Dostosowywanie wywoływanych otok COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d1f74-117">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="d1f74-118">Opisuje, <xref:System.Runtime.InteropServices.MarshalAsAttribute> jak jawnie zorganizować typy danych przy użyciu atrybutu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="d1f74-118">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="d1f74-119">[Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d1f74-119">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="d1f74-120">Opisuje sposób dostosowywania zachowania związanego z kierowaniem typów w zestawie międzyoperacyjnym i sposób ręcznego definiowania typów COM.</span><span class="sxs-lookup"><span data-stu-id="d1f74-120">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="d1f74-121">[Zaawansowana współdziałanie COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d1f74-121">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="d1f74-122">Zawiera łącza do dodatkowych informacji na temat dołączania składników COM do aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d1f74-122">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="d1f74-123">[Podsumowanie konwersji zestawu na bibliotekę typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d1f74-123">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="d1f74-124">Opisuje zestaw do procesu konwersji eksportu biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="d1f74-124">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="d1f74-125">[Podsumowanie dotyczące konwersji biblioteki typów na zestaw](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d1f74-125">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="d1f74-126">Opisuje proces konwersji biblioteki typów na import zestawu.</span><span class="sxs-lookup"><span data-stu-id="d1f74-126">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="d1f74-127">[Współdziałanie przy użyciu typów ogólnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d1f74-127">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="d1f74-128">Opisuje, które akcje są obsługiwane w przypadku używania typów ogólnych do współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="d1f74-128">Describes which actions are supported when using generic types for COM interoperability.</span></span>
