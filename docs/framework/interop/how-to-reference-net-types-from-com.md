---
title: 'Porady: odwołania do typów .NET z modelu COM'
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
ms.openlocfilehash: 0223cb25b933cc84af49aa86d90259fdf1fd3efc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124172"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="87022-102">Porady: odwołania do typów .NET z modelu COM</span><span class="sxs-lookup"><span data-stu-id="87022-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="87022-103">Z punktu widzenia kodu klienta i serwera różnice między modelem COM i .NET Framework są bardzo niewidoczne.</span><span class="sxs-lookup"><span data-stu-id="87022-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="87022-104">Klienci programu Microsoft Visual Basic mogą wyświetlać obiekt .NET w przeglądarce obiektów, która udostępnia metody obiektu i składnię, właściwości i pola dokładnie tak, jakby były dowolnym innym obiektem COM.</span><span class="sxs-lookup"><span data-stu-id="87022-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="87022-105">Proces importowania biblioteki typów jest nieco bardziej skomplikowany dla C++ klientów, chociaż te same narzędzia są używane do eksportowania metadanych do biblioteki typów com.</span><span class="sxs-lookup"><span data-stu-id="87022-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="87022-106">Aby odwołać się do elementów członkowskich obiektu C++ platformy .NET z niezarządzanego klienta, należy odwołać się do pliku TLB (utworzonego za pomocą Tlbexp. exe) z dyrektywą **#import** .</span><span class="sxs-lookup"><span data-stu-id="87022-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="87022-107">W przypadku odwoływania się do C++biblioteki typów z, należy określić opcję **raw_interfaces_only** lub zaimportować definicje w bibliotece klas podstawowych, mscorlib. tlb.</span><span class="sxs-lookup"><span data-stu-id="87022-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="87022-108">Aby zaimportować bibliotekę</span><span class="sxs-lookup"><span data-stu-id="87022-108">To import a library</span></span>  
  
- <span data-ttu-id="87022-109">Określ opcję **raw_interfaces_only** w dyrektywie **#import** .</span><span class="sxs-lookup"><span data-stu-id="87022-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="87022-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="87022-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="87022-111">—lub—</span><span class="sxs-lookup"><span data-stu-id="87022-111">-or-</span></span>  
  
- <span data-ttu-id="87022-112">Uwzględnij #import dyrektywę dla biblioteki mscorlib. tlb.</span><span class="sxs-lookup"><span data-stu-id="87022-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="87022-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="87022-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="87022-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87022-114">See also</span></span>

- [<span data-ttu-id="87022-115">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="87022-115">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="87022-116">Rejestrowanie zestawów do użycia z modelem COM</span><span class="sxs-lookup"><span data-stu-id="87022-116">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="87022-117">[Wywołanie obiektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87022-117">[Calling a .NET Object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="87022-118">[Wdrażanie aplikacji na potrzeby dostępu do modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87022-118">[Deploying an Application for COM Access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
