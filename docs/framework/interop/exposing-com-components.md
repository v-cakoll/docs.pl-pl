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
ms.openlocfilehash: f644e4f4ff47e31c0f2aaadb577aa6715b445d29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388225"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="69b0d-102">Udostępnianie składników COM programowi.NET Framework</span><span class="sxs-lookup"><span data-stu-id="69b0d-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="69b0d-103">Ta sekcja zawiera podsumowanie procesu potrzebne do udostępnienia istniejących składnika modelu COM z kodem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="69b0d-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="69b0d-104">Aby uzyskać informacje na temat pisania serwerów COM to ściśle zintegrowane z programu .NET Framework, zobacz [projektowania współdziałanie](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="69b0d-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100)).</span></span>
  
 <span data-ttu-id="69b0d-105">Istniejące składniki COM są cenne zasoby pozostają dostępne w zarządzanym kodzie jako biznesowym warstwy środkowej aplikacje lub funkcje izolowanym.</span><span class="sxs-lookup"><span data-stu-id="69b0d-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="69b0d-106">Składnik idealne ma podstawowego zestawu międzyoperacyjnego i ściśle zgodne ze standardami programowania narzucone przez COM.</span><span class="sxs-lookup"><span data-stu-id="69b0d-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="69b0d-107">Aby udostępnić składników modelu COM aplikacji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="69b0d-107">To expose COM components to the .NET Framework</span></span>  
  
1.  <span data-ttu-id="69b0d-108">[Importowanie biblioteki typów jako zestawu](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="69b0d-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="69b0d-109">Środowisko uruchomieniowe języka wspólnego wymaga metadanych dla wszystkich typów, w tym typy COM.</span><span class="sxs-lookup"><span data-stu-id="69b0d-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="69b0d-110">Istnieje kilka sposobów można uzyskać zestawu zawierającego typów COM zaimportowana jako metadanych.</span><span class="sxs-lookup"><span data-stu-id="69b0d-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2.  <span data-ttu-id="69b0d-111">[Tworzenie typów COM w kodzie zarządzanym](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="69b0d-111">[Create COM types in managed Code](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span></span>  
  
     <span data-ttu-id="69b0d-112">Można sprawdzić typów COM, aktywować wystąpień i wywołania metod w obiekcie COM w taki sam sposób jak w przypadku dowolnego typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="69b0d-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3.  <span data-ttu-id="69b0d-113">[Kompilowanie projektu międzyoperacyjnego](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="69b0d-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="69b0d-114">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Zapewnia kilka języków zgodne z wspólnego języka specyfikacji (ze specyfikacją CLS), łącznie z kompilatorów [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# i C++.</span><span class="sxs-lookup"><span data-stu-id="69b0d-114">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides compilers for several languages compliant with the Common Language Specification (CLS), including [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++.</span></span>  
  
4.  <span data-ttu-id="69b0d-115">[Wdrażanie aplikacji międzyoperacyjnych](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="69b0d-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="69b0d-116">Aplikacje międzyoperacyjne najlepiej są wdrażane jako [o silnych nazwach](../app-domains/strong-named-assemblies.md), podpisany zestawów w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="69b0d-116">Interop applications are best deployed as [strong-named](../app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b0d-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69b0d-117">See Also</span></span>  
 [<span data-ttu-id="69b0d-118">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="69b0d-118">Interoperating with Unmanaged Code</span></span>](index.md)  
 <span data-ttu-id="69b0d-119">[Zagadnienia dotyczące projektowania dla współdziałanie](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="69b0d-119">[Design Considerations for Interoperation](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100))</span></span>  
 [<span data-ttu-id="69b0d-120">Przykład międzyoperacyjnego modelu COM: Klient modelu .NET i serwer COM</span><span class="sxs-lookup"><span data-stu-id="69b0d-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)  
 [<span data-ttu-id="69b0d-121">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="69b0d-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="69b0d-122">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="69b0d-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
