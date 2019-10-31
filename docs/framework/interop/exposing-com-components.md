---
title: Udostępnianie składników COM programowi.NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
ms.openlocfilehash: 914f72b5e4840555541943620ca2df1f629b0604
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123524"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="d8e79-102">Udostępnianie składników COM programowi.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d8e79-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="d8e79-103">Ta sekcja podsumowuje proces, który jest wymagany, aby uwidocznić istniejący składnik COM w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d8e79-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="d8e79-104">Aby uzyskać szczegółowe informacje na temat pisania serwerów COM, które ścisłie integrują się z .NET Framework, zobacz [zagadnienia dotyczące projektowania współdziałania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d8e79-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="d8e79-105">Istniejące składniki modelu COM są cennymi zasobami w kodzie zarządzanym jako aplikacje biznesowe warstwy środkowej lub jako izolowane funkcje.</span><span class="sxs-lookup"><span data-stu-id="d8e79-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="d8e79-106">Idealny składnik ma podstawowy zestaw międzyoperacyjny i jest zgodny ze standardami programistycznymi nałożonymi przez model COM.</span><span class="sxs-lookup"><span data-stu-id="d8e79-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="d8e79-107">Aby uwidocznić składniki COM .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d8e79-107">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="d8e79-108">[Zaimportuj bibliotekę typów jako zestaw](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="d8e79-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="d8e79-109">Środowisko uruchomieniowe języka wspólnego wymaga metadanych dla wszystkich typów, w tym typów COM.</span><span class="sxs-lookup"><span data-stu-id="d8e79-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="d8e79-110">Istnieje kilka sposobów uzyskania zestawu zawierającego typy COM zaimportowane jako metadane.</span><span class="sxs-lookup"><span data-stu-id="d8e79-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="d8e79-111">[Używaj typów com w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d8e79-111">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="d8e79-112">Można sprawdzić typy COM, uaktywnić wystąpienia i wywołać metody obiektu COM w taki sam sposób, jak w przypadku dowolnego typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d8e79-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="d8e79-113">[Kompiluj projekt międzyoperacyjności](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="d8e79-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="d8e79-114">Windows SDK zapewnia kompilatory dla kilku języków zgodnych z Common Language Specification (CLS), w tym Visual Basic, C#i C++.</span><span class="sxs-lookup"><span data-stu-id="d8e79-114">The Windows SDK provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="d8e79-115">[Wdróż aplikację międzyoperacyjną](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="d8e79-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="d8e79-116">Aplikacje międzyoperacyjności najlepiej wdrożyć jako podpisane zestawy [o silnych nazwach](../../standard/assembly/strong-named.md)w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="d8e79-116">Interop applications are best deployed as [strong-named](../../standard/assembly/strong-named.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8e79-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8e79-117">See also</span></span>

- [<span data-ttu-id="d8e79-118">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="d8e79-118">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="d8e79-119">[Zagadnienia dotyczące projektowania operacji międzyoperacyjnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d8e79-119">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="d8e79-120">Przykład międzyoperacyjnego modelu COM: Klient modelu .NET i serwer COM</span><span class="sxs-lookup"><span data-stu-id="d8e79-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="d8e79-121">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="d8e79-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="d8e79-122">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="d8e79-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
