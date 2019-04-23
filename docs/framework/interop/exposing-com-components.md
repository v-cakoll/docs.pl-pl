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
ms.openlocfilehash: 2b7aa028afeaf4230ee079f0d4071a5cd6a21c65
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320915"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="e7112-102">Udostępnianie składników COM programowi.NET Framework</span><span class="sxs-lookup"><span data-stu-id="e7112-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="e7112-103">Ta sekcja zawiera podsumowanie procesu potrzebne, aby udostępnić istniejący składnik COM do zarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="e7112-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="e7112-104">Aby uzyskać informacje na temat pisania serwerów COM, który jest ściśle zintegrowane z .NET Framework, zobacz [zagadnień projektowych dotyczących współdziałanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e7112-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="e7112-105">Istniejących składników COM są cenne zasoby w zarządzanym kodzie jako aplikacje biznesowe warstwy środkowej lub funkcje izolowanego.</span><span class="sxs-lookup"><span data-stu-id="e7112-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="e7112-106">Idealnym rozwiązaniem składnik zawiera podstawowy zestaw międzyoperacyjny i ściśle odpowiada programowania Standardy nakładane przez model COM.</span><span class="sxs-lookup"><span data-stu-id="e7112-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="e7112-107">Aby udostępnić składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e7112-107">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="e7112-108">[Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="e7112-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="e7112-109">Środowisko uruchomieniowe języka wspólnego wymaga metadanych dla wszystkich typów, w tym typy modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e7112-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="e7112-110">Istnieje kilka sposobów, aby uzyskać zestaw zawierający typy modelu COM importowanych w metadanych.</span><span class="sxs-lookup"><span data-stu-id="e7112-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="e7112-111">[Używanie typów modelu COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e7112-111">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="e7112-112">Można sprawdzić typy modelu COM, aktywować wystąpienia i wywoływać metody na obiekt COM w taki sam sposób jak w przypadku dowolnego typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e7112-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="e7112-113">[Kompilowanie projektu międzyoperacyjnego](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="e7112-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="e7112-114">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Udostępnia kompilatory dla kilku języków zgodny z Common Language Specification (CLS), w tym [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#i C++.</span><span class="sxs-lookup"><span data-stu-id="e7112-114">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides compilers for several languages compliant with the Common Language Specification (CLS), including [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++.</span></span>  
  
4. <span data-ttu-id="e7112-115">[Wdrażanie aplikacji międzyoperacyjnych](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="e7112-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="e7112-116">Aplikacje międzyoperacyjne najlepiej są wdrażane jako [o silnej nazwie](../app-domains/strong-named-assemblies.md), podpisane zestawów w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="e7112-116">Interop applications are best deployed as [strong-named](../app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7112-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7112-117">See also</span></span>

- [<span data-ttu-id="e7112-118">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="e7112-118">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="e7112-119">[Zagadnienia dotyczące projektowania do celów międzyoperacyjności](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e7112-119">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="e7112-120">Przykład międzyoperacyjnego modelu COM: Klient modelu .NET i serwer COM</span><span class="sxs-lookup"><span data-stu-id="e7112-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="e7112-121">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="e7112-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="e7112-122">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="e7112-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
