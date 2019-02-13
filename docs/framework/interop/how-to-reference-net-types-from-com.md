---
title: 'Instrukcje: Odwołanie do typów .NET z modelu COM'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5151d89feccbe68daa5a8de4aa3b75a42511899
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220273"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="92683-102">Instrukcje: Odwołanie do typów .NET z modelu COM</span><span class="sxs-lookup"><span data-stu-id="92683-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="92683-103">Z punktu widzenia kodu klienta i serwera różnice w modelu COM i .NET Framework są niewidoczne w dużej mierze.</span><span class="sxs-lookup"><span data-stu-id="92683-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="92683-104">Klienci programu Microsoft Visual Basic można wyświetlić obiektu platformy .NET w przeglądarce obiektów, który udostępnia metody obiektu i składnię, właściwości i pola, dokładnie tak jak w przypadku dowolnego obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="92683-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="92683-105">Proces importowania biblioteki typów jest nieco bardziej skomplikowanego dla klientów w języku C++, mimo że Eksportowanie metadanych do biblioteki typów COM za pomocą tych samych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="92683-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="92683-106">Aby odwołać elementach członkowskich obiektu .NET z niezarządzanego klienta języka C++, odwołaj się do TLB pliku (utworzone za pomocą Tlbexp.exe) za pomocą **#import** dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="92683-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="92683-107">Podczas odwoływania się do biblioteki typów, z języka C++, należy określić **raw_interfaces_only —** opcję lub zaimportować definicje w bibliotece klasy bazowej Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="92683-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="92683-108">Aby zaimportować bibliotekę</span><span class="sxs-lookup"><span data-stu-id="92683-108">To import a library</span></span>  
  
-   <span data-ttu-id="92683-109">Określ **raw_interfaces_only —** opcji **#import** dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="92683-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="92683-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="92683-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="92683-111">—lub—</span><span class="sxs-lookup"><span data-stu-id="92683-111">-or-</span></span>  
  
-   <span data-ttu-id="92683-112">#Import — dyrektywa zawierają Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="92683-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="92683-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="92683-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="92683-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92683-114">See also</span></span>
- [<span data-ttu-id="92683-115">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="92683-115">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="92683-116">Rejestrowanie zestawów do użycia z modelem COM</span><span class="sxs-lookup"><span data-stu-id="92683-116">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="92683-117">[Wywołanie obiektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="92683-117">[Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="92683-118">[Wdrażanie aplikacji dla dostępu do modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="92683-118">[Deploying an Application for COM Access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
