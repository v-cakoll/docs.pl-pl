---
title: Udostępnianie składników COM programowi.NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20ec022f378feba3368ea79fdd5c6ee7ecccf1b9
ms.sourcegitcommit: 56ac30a336668124cb7d95d8ace16bd985875147
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469661"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="d3b03-102">Udostępnianie składników COM programowi.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d3b03-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="d3b03-103">Ta sekcja zawiera podsumowanie procesu potrzebne, aby udostępnić istniejący składnik COM do zarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="d3b03-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="d3b03-104">Aby uzyskać informacje na temat pisania serwerów COM, który jest ściśle zintegrowane z .NET Framework, zobacz [zagadnień projektowych dotyczących współdziałanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d3b03-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="d3b03-105">Istniejących składników COM są cenne zasoby w zarządzanym kodzie jako aplikacje biznesowe warstwy środkowej lub funkcje izolowanego.</span><span class="sxs-lookup"><span data-stu-id="d3b03-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="d3b03-106">Idealnym rozwiązaniem składnik zawiera podstawowy zestaw międzyoperacyjny i ściśle odpowiada programowania Standardy nakładane przez model COM.</span><span class="sxs-lookup"><span data-stu-id="d3b03-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="d3b03-107">Aby udostępnić składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d3b03-107">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="d3b03-108">[Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="d3b03-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="d3b03-109">Środowisko uruchomieniowe języka wspólnego wymaga metadanych dla wszystkich typów, w tym typy modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d3b03-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="d3b03-110">Istnieje kilka sposobów, aby uzyskać zestaw zawierający typy modelu COM importowanych w metadanych.</span><span class="sxs-lookup"><span data-stu-id="d3b03-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="d3b03-111">[Używanie typów modelu COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d3b03-111">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="d3b03-112">Można sprawdzić typy modelu COM, aktywować wystąpienia i wywoływać metody na obiekt COM w taki sam sposób jak w przypadku dowolnego typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d3b03-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="d3b03-113">[Kompilowanie projektu międzyoperacyjnego](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="d3b03-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="d3b03-114">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Udostępnia kompilatory dla kilku języków zgodny z Common Language Specification (CLS), w tym Visual Basic C#, i C++.</span><span class="sxs-lookup"><span data-stu-id="d3b03-114">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="d3b03-115">[Wdrażanie aplikacji międzyoperacyjnych](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="d3b03-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="d3b03-116">Aplikacje międzyoperacyjne najlepiej są wdrażane jako [o silnej nazwie](../app-domains/strong-named-assemblies.md), podpisane zestawów w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d3b03-116">Interop applications are best deployed as [strong-named](../app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b03-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3b03-117">See also</span></span>

- [<span data-ttu-id="d3b03-118">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="d3b03-118">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="d3b03-119">[Zagadnienia dotyczące projektowania do celów międzyoperacyjności](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d3b03-119">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="d3b03-120">Przykład międzyoperacyjnego modelu COM: Klient modelu .NET i serwer COM</span><span class="sxs-lookup"><span data-stu-id="d3b03-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="d3b03-121">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="d3b03-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="d3b03-122">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="d3b03-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
