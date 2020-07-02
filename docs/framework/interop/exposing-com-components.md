---
title: Udostępnianie składników COM programowi.NET Framework
description: Poznaj proces udostępniania składników COM na platformie .NET. Składniki COM są cenne w kodzie zarządzanym jako aplikacje biznesowe warstwy środkowej lub izolowane.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
ms.openlocfilehash: 459ba7ffed2e4f6c458f89a63b2baa37180d270d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620849"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="3937d-104">Udostępnianie składników COM programowi.NET Framework</span><span class="sxs-lookup"><span data-stu-id="3937d-104">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="3937d-105">Ta sekcja podsumowuje proces, który jest wymagany, aby uwidocznić istniejący składnik COM w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="3937d-105">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="3937d-106">Aby uzyskać szczegółowe informacje na temat pisania serwerów COM, które ścisłie integrują się z .NET Framework, zobacz [zagadnienia dotyczące projektowania współdziałania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3937d-106">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="3937d-107">Istniejące składniki modelu COM są cennymi zasobami w kodzie zarządzanym jako aplikacje biznesowe warstwy środkowej lub jako izolowane funkcje.</span><span class="sxs-lookup"><span data-stu-id="3937d-107">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="3937d-108">Idealny składnik ma podstawowy zestaw międzyoperacyjny i jest zgodny ze standardami programistycznymi nałożonymi przez model COM.</span><span class="sxs-lookup"><span data-stu-id="3937d-108">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="3937d-109">Aby uwidocznić składniki COM .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3937d-109">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="3937d-110">[Zaimportuj bibliotekę typów jako zestaw](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="3937d-110">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="3937d-111">Środowisko uruchomieniowe języka wspólnego wymaga metadanych dla wszystkich typów, w tym typów COM.</span><span class="sxs-lookup"><span data-stu-id="3937d-111">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="3937d-112">Istnieje kilka sposobów uzyskania zestawu zawierającego typy COM zaimportowane jako metadane.</span><span class="sxs-lookup"><span data-stu-id="3937d-112">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="3937d-113">[Używaj typów com w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3937d-113">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="3937d-114">Można sprawdzić typy COM, uaktywnić wystąpienia i wywołać metody obiektu COM w taki sam sposób, jak w przypadku dowolnego typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3937d-114">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="3937d-115">[Kompiluj projekt międzyoperacyjności](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="3937d-115">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="3937d-116">Windows SDK zapewnia kompilatory dla kilku języków zgodnych z Common Language Specification (CLS), w tym Visual Basic, C# i C++.</span><span class="sxs-lookup"><span data-stu-id="3937d-116">The Windows SDK provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="3937d-117">[Wdróż aplikację międzyoperacyjną](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="3937d-117">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="3937d-118">Aplikacje międzyoperacyjności najlepiej wdrożyć jako podpisane zestawy [o silnych nazwach](../../standard/assembly/strong-named.md)w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="3937d-118">Interop applications are best deployed as [strong-named](../../standard/assembly/strong-named.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3937d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3937d-119">See also</span></span>

- [<span data-ttu-id="3937d-120">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="3937d-120">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="3937d-121">[Zagadnienia dotyczące projektowania operacji międzyoperacyjnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3937d-121">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="3937d-122">Przykład międzyoperacyjnego modelu COM: klient modelu COM i serwer COM</span><span class="sxs-lookup"><span data-stu-id="3937d-122">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="3937d-123">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="3937d-123">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="3937d-124">Gacutil.exe (Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="3937d-124">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
