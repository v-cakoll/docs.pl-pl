---
title: "Porady: odwołania do typów .NET z modelu COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b452dd686286ba0ddf648ee532e67a0c121f66eb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="34308-102">Porady: odwołania do typów .NET z modelu COM</span><span class="sxs-lookup"><span data-stu-id="34308-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="34308-103">Z punktu widzenia kodu klienta i serwera różnice między COM i .NET Framework są przede wszystkim niewidoczne.</span><span class="sxs-lookup"><span data-stu-id="34308-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="34308-104">Microsoft Visual Basic klientów można wyświetlić obiektu .NET. w przeglądarce obiektów, który udostępnia metody obiektu i składni, właściwości oraz polach dokładnie tak, jakby była innego obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="34308-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="34308-105">Importowanie biblioteki typów jest nieco trudniejsze dla klientów C++, mimo że Eksportowanie metadanych do biblioteki typów COM za pomocą tych samych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="34308-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="34308-106">Aby odwołać elementy członkowskie programu .NET obiektu z niezarządzanego klienta C++, odwołania pliku TLB (realizowane z Tlbexp.exe) z **#import** dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="34308-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="34308-107">Podczas odwoływania się do biblioteki typów, z C++, należy określić **raw_interfaces_only —** opcji lub zaimportować definicje w bibliotece klasy podstawowej Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="34308-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="34308-108">Aby zaimportować bibliotekę</span><span class="sxs-lookup"><span data-stu-id="34308-108">To import a library</span></span>  
  
-   <span data-ttu-id="34308-109">Określ **raw_interfaces_only —** opcji **#import** dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="34308-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="34308-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="34308-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="34308-111">—lub—</span><span class="sxs-lookup"><span data-stu-id="34308-111">-or-</span></span>  
  
-   <span data-ttu-id="34308-112">Include — dyrektywa #import dla Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="34308-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="34308-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="34308-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="34308-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34308-114">See Also</span></span>  
 [<span data-ttu-id="34308-115">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="34308-115">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="34308-116">Rejestrowanie zestawów do użycia z modelem COM</span><span class="sxs-lookup"><span data-stu-id="34308-116">Registering Assemblies with COM</span></span>](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [<span data-ttu-id="34308-117">Wywołanie obiektu .NET.</span><span class="sxs-lookup"><span data-stu-id="34308-117">Calling a .NET Object</span></span>](http://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
 [<span data-ttu-id="34308-118">Wdrażanie aplikacji na potrzeby dostępu modelu COM</span><span class="sxs-lookup"><span data-stu-id="34308-118">Deploying an Application for COM Access</span></span>](http://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce)
