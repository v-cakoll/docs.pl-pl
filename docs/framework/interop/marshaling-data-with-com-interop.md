---
title: Marshaling danych za pomocą modelu COM
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0d94223223568efe921af3a340815a966cc6c6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="0497d-102">Marshaling danych za pomocą modelu COM</span><span class="sxs-lookup"><span data-stu-id="0497d-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="0497d-103">Współdziałanie z COM zapewnia obsługę zarówno przy użyciu obiektów COM z kodu zarządzanego i udostępnianie zarządzane obiekty do modelu COM.</span><span class="sxs-lookup"><span data-stu-id="0497d-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="0497d-104">Obsługa przekazywanie danych do i z modelu COM jest rozbudowana i prawie zawsze zawiera poprawne zachowanie marshalingu.</span><span class="sxs-lookup"><span data-stu-id="0497d-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="0497d-105">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Obejmuje następujące narzędzia międzyoperacyjnego COM:</span><span class="sxs-lookup"><span data-stu-id="0497d-105">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] includes the following COM interop tools:</span></span>  
  
-   <span data-ttu-id="0497d-106">[Importer biblioteki (Tlbimp.exe) wpisz](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), który konwertuje Biblioteka typów COM do zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="0497d-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="0497d-107">Z tego zestawu interop organizowanie usługi generuje otoki wykonujących przekazywanie między zarządzanymi i niezarządzanymi pamięci danych.</span><span class="sxs-lookup"><span data-stu-id="0497d-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
-   <span data-ttu-id="0497d-108">[Eksporter biblioteki (Tlbexp.exe) wpisz](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), która tworzy bibliotekę typów COM z zestawu i generuje otoki, który wykonuje przekazywanie podczas wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="0497d-108">[Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="0497d-109">Poniższe sekcje łącza do tematów opisujących procesów dostosowywania otoki międzyoperacyjnego, jeśli można lub musi podasz organizatora typu dodatkowe informacje.</span><span class="sxs-lookup"><span data-stu-id="0497d-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0497d-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0497d-110">In This Section</span></span>  
<span data-ttu-id="0497d-111">[Porady: ręczne tworzenie otok](how-to-create-wrappers-manually.md) </span><span class="sxs-lookup"><span data-stu-id="0497d-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) </span></span>  
<span data-ttu-id="0497d-112">Opisuje sposób tworzenia otoki COM ręcznie w kodzie źródłowym zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="0497d-112">Describes how to create a COM wrapper manually in managed source code.</span></span> 
 
 [<span data-ttu-id="0497d-113">Instrukcje: Migrowanie zarządzanego kodu DCOM do WCF</span><span class="sxs-lookup"><span data-stu-id="0497d-113">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="0497d-114">Opisuje sposób Migrowanie zarządzanego kodu DCOM do WCF dla najbardziej bezpieczne rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0497d-114">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0497d-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0497d-115">Related Sections</span></span>  
 <span data-ttu-id="0497d-116">[Typy danych modelu COM](https://msdn.microsoft.com/library/sak564ww(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0497d-116">[COM Data Types](https://msdn.microsoft.com/library/sak564ww(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0497d-117">Zawiera odpowiednie typy zarządzane i niezarządzane danych.</span><span class="sxs-lookup"><span data-stu-id="0497d-117">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="0497d-118">[Dostosowywanie wywoływane otoki COM](https://msdn.microsoft.com/library/3bwc828w(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0497d-118">[Customizing COM Callable Wrappers](https://msdn.microsoft.com/library/3bwc828w(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0497d-119">Opisuje sposób jawnie kierować typy danych przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="0497d-119">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="0497d-120">[Dostosowywanie wywoływane otoki środowiska uruchomieniowego](https://msdn.microsoft.com/library/e753eftz(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0497d-120">[Customizing Runtime Callable Wrappers](https://msdn.microsoft.com/library/e753eftz(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0497d-121">Opisuje sposób dostosować zachowanie marshalingu typów z zestawu międzyoperacyjnego oraz definiowanie typów COM ręcznie.</span><span class="sxs-lookup"><span data-stu-id="0497d-121">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="0497d-122">[Współdziałanie COM zaawansowane](https://msdn.microsoft.com/library/bd9cdfyx(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0497d-122">[Advanced COM Interoperability](https://msdn.microsoft.com/library/bd9cdfyx(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0497d-123">Zawiera łącza do dodatkowych informacji o włączenie składniki modelu COM aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0497d-123">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="0497d-124">[Zestaw do typu biblioteki konwersja — podsumowanie](https://msdn.microsoft.com/library/xk1120c3(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0497d-124">[Assembly to Type Library Conversion Summary](https://msdn.microsoft.com/library/xk1120c3(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0497d-125">Zawiera opis zestawu na typ procesu konwersji eksportu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0497d-125">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="0497d-126">[Biblioteki typów na zestaw konwersja — podsumowanie](https://msdn.microsoft.com/library/k83zzh38(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0497d-126">[Type Library to Assembly Conversion Summary](https://msdn.microsoft.com/library/k83zzh38(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0497d-127">W tym artykule opisano bibliotekę typów, aby proces konwersji importu zestawu.</span><span class="sxs-lookup"><span data-stu-id="0497d-127">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="0497d-128">[Współdziałanie za pomocą typów ogólnych](https://msdn.microsoft.com/library/ms229590(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="0497d-128">[Interoperating Using Generic Types](https://msdn.microsoft.com/library/ms229590(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="0497d-129">Opisuje akcje, które są obsługiwane w przypadku współdziałania COM za pomocą typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="0497d-129">Describes which actions are supported when using generic types for COM interoperability.</span></span>
