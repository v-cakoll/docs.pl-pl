---
title: 'Instrukcje: Odwołania do typów .NET z modelu COM'
description: Odwołuj się do typów .NET z modelu COM. Klienci VB mogą wyświetlać obiekt .NET w przeglądarce obiektów, ale klienci C++ muszą odwoływać się do pliku TLB przy użyciu \# dyrektywy import.
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
ms.openlocfilehash: f8d052c7b9bac9c4bab61ab1950e9e89a7c73912
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618964"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="ade12-104">Instrukcje: Odwołania do typów .NET z modelu COM</span><span class="sxs-lookup"><span data-stu-id="ade12-104">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="ade12-105">Z punktu widzenia kodu klienta i serwera różnice między modelem COM i .NET Framework są bardzo niewidoczne.</span><span class="sxs-lookup"><span data-stu-id="ade12-105">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="ade12-106">Klienci programu Microsoft Visual Basic mogą wyświetlać obiekt .NET w przeglądarce obiektów, która udostępnia metody obiektu i składnię, właściwości i pola dokładnie tak, jakby były dowolnym innym obiektem COM.</span><span class="sxs-lookup"><span data-stu-id="ade12-106">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="ade12-107">Proces importowania biblioteki typów jest nieco bardziej skomplikowany dla klientów C++, chociaż te same narzędzia są używane do eksportowania metadanych do biblioteki typów COM.</span><span class="sxs-lookup"><span data-stu-id="ade12-107">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="ade12-108">Aby odwołać się do elementów członkowskich obiektu platformy .NET z niezarządzanego klienta C++, należy odwołać się do pliku TLB (utworzonego za pomocą Tlbexp.exe) za pomocą dyrektywy **#import** .</span><span class="sxs-lookup"><span data-stu-id="ade12-108">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="ade12-109">W przypadku odwoływania się do biblioteki typów z C++ należy określić opcję **raw_interfaces_only** lub zaimportować definicje w bibliotece klas bazowych, mscorlib. tlb.</span><span class="sxs-lookup"><span data-stu-id="ade12-109">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="ade12-110">Aby zaimportować bibliotekę</span><span class="sxs-lookup"><span data-stu-id="ade12-110">To import a library</span></span>  
  
- <span data-ttu-id="ade12-111">W dyrektywie **#import** określ opcję **raw_interfaces_only** .</span><span class="sxs-lookup"><span data-stu-id="ade12-111">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="ade12-112">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ade12-112">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="ade12-113">-lub-</span><span class="sxs-lookup"><span data-stu-id="ade12-113">-or-</span></span>  
  
- <span data-ttu-id="ade12-114">Uwzględnij #import dyrektywę dla biblioteki mscorlib. tlb.</span><span class="sxs-lookup"><span data-stu-id="ade12-114">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="ade12-115">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ade12-115">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ade12-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ade12-116">See also</span></span>

- [<span data-ttu-id="ade12-117">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="ade12-117">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="ade12-118">Rejestrowanie zestawów do użycia z modelem COM</span><span class="sxs-lookup"><span data-stu-id="ade12-118">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="ade12-119">[Wywołanie obiektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ade12-119">[Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="ade12-120">[Wdrażanie aplikacji na potrzeby dostępu do modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ade12-120">[Deploying an Application for COM Access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
