---
title: Organizowanie danych za pomocą modelu COM
description: Zapoznaj się z artykułami dotyczącymi organizowania danych z międzyoperacyjnym modelem COM. Narzędzia Tlbimp.exe i Tlbexp.exe są konwertowane między biblioteką typów modelu COM i zestawem międzyoperacyjnym.
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: eedfb60a75e2fe5fafdaa786dbb54adddf28400e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621512"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="d3770-104">Organizowanie danych za pomocą modelu COM</span><span class="sxs-lookup"><span data-stu-id="d3770-104">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="d3770-105">Współdziałanie modelu COM zapewnia obsługę zarówno obiektów COM z kodu zarządzanego, jak i Uwidacznianie obiektów zarządzanych w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d3770-105">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="d3770-106">Obsługa przekazywania danych do i z modelu COM jest obszerna i prawie zawsze zapewnia prawidłowe zachowanie organizowania.</span><span class="sxs-lookup"><span data-stu-id="d3770-106">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="d3770-107">Windows SDK obejmuje następujące narzędzia międzyoperacyjności modelu COM:</span><span class="sxs-lookup"><span data-stu-id="d3770-107">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="d3770-108">[Importer biblioteki typów (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), który konwertuje bibliotekę typów com na zestaw międzyoperacyjny.</span><span class="sxs-lookup"><span data-stu-id="d3770-108">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="d3770-109">Z tego zestawu usługa Marshaling Interop generuje otoki, które wykonują kierowanie danych między zarządzaną i niezarządzaną pamięcią.</span><span class="sxs-lookup"><span data-stu-id="d3770-109">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="d3770-110">[Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), który tworzy bibliotekę typów com z zestawu i generuje otokę wykonującą operacje organizowania podczas wywołań metod.</span><span class="sxs-lookup"><span data-stu-id="d3770-110">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="d3770-111">W poniższych sekcjach znajdują się łącza do tematów opisujących procesy dostosowywania otok międzyoperacyjnych, gdy użytkownik może (lub musi) dostarczyć Organizatorowi dodatkowe informacje o typie.</span><span class="sxs-lookup"><span data-stu-id="d3770-111">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3770-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d3770-112">In This Section</span></span>  
<span data-ttu-id="d3770-113">[Instrukcje: ręczne tworzenie otok](how-to-create-wrappers-manually.md) Opisuje sposób ręcznego tworzenia otoki COM w zarządzanym kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="d3770-113">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="d3770-114">Instrukcje: Migrowanie zarządzanego kodu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="d3770-114">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="d3770-115">Opisuje sposób migrowania zarządzanego kodu DCOM do usługi WCF w celu zapewnienia najbezpieczniejszego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d3770-115">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d3770-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d3770-116">Related Sections</span></span>  
 <span data-ttu-id="d3770-117">[Typy danych COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d3770-117">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="d3770-118">Zapewnia odpowiednie zarządzane i niezarządzane typy danych.</span><span class="sxs-lookup"><span data-stu-id="d3770-118">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="d3770-119">[Dostosowywanie wywoływanych otok COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d3770-119">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="d3770-120">Opisuje, jak jawnie zorganizować typy danych przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="d3770-120">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="d3770-121">[Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d3770-121">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="d3770-122">Opisuje sposób dostosowywania zachowania związanego z kierowaniem typów w zestawie międzyoperacyjnym i sposób ręcznego definiowania typów COM.</span><span class="sxs-lookup"><span data-stu-id="d3770-122">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="d3770-123">[Zaawansowana współdziałanie COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d3770-123">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="d3770-124">Zawiera łącza do dodatkowych informacji na temat dołączania składników COM do aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d3770-124">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="d3770-125">[Podsumowanie konwersji zestawu na bibliotekę typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d3770-125">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="d3770-126">Opisuje zestaw do procesu konwersji eksportu biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="d3770-126">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="d3770-127">[Podsumowanie dotyczące konwersji biblioteki typów na zestaw](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d3770-127">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="d3770-128">Opisuje proces konwersji biblioteki typów na import zestawu.</span><span class="sxs-lookup"><span data-stu-id="d3770-128">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="d3770-129">[Współdziałanie przy użyciu typów ogólnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d3770-129">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="d3770-130">Opisuje, które akcje są obsługiwane w przypadku używania typów ogólnych do współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="d3770-130">Describes which actions are supported when using generic types for COM interoperability.</span></span>
