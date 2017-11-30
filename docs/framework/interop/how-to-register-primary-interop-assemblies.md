---
title: "Porady: rejestrowanie podstawowych zestawów międzyoperacyjnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b72a24f349237aa35ccae295e9e552facc21ddd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-register-primary-interop-assemblies"></a><span data-ttu-id="f6eb7-102">Porady: rejestrowanie podstawowych zestawów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="f6eb7-102">How to: Register Primary Interop Assemblies</span></span>
<span data-ttu-id="f6eb7-103">Klasy mogą być organizowany tylko przy użyciu współdziałanie z COM i zawsze są przekazywane jako interfejsy.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-103">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="f6eb7-104">W niektórych przypadkach interfejs używany do organizowania klasy nosi nazwę interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-104">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="f6eb7-105">Aby dowiedzieć się, jak zastępowanie interfejsu klasy przy użyciu interfejsu wybranych przez użytkownika, zobacz [wywoływana otoka COM](../../../docs/framework/interop/com-callable-wrapper.md).</span><span class="sxs-lookup"><span data-stu-id="f6eb7-105">For information about overriding the class interface with an interface of your choice, see [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md).</span></span>  
  
 <span data-ttu-id="f6eb7-106">Mimo że każdy Deweloper, który chce używać typów COM aplikacji .NET Framework, można wygenerować zestawu międzyoperacyjnego, to tworzy tak problem.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-106">Although any developer who wants to use COM types from a .NET Framework application can generate an interop assembly, doing so creates a problem.</span></span> <span data-ttu-id="f6eb7-107">Zawsze dewelopera importuje i podpisuje Biblioteka typów COM, który developer tworzy zestaw unikatowy typów, które są zgodne z tymi zaimportowane i podpisany przez inny dewelopera.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-107">Each time a developer imports and signs a COM type library, that developer creates a set of unique types that are incompatible with those imported and signed by another developer.</span></span> <span data-ttu-id="f6eb7-108">Rozwiązanie tego problemu niezgodności typu jest dla wszystkich deweloperów uzyskanie dostarczonego przez dostawcę i podpisany podstawowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-108">The solution to this type incompatibility problem is for each developer to obtain the vendor-supplied and signed primary interop assembly.</span></span>  
  
 <span data-ttu-id="f6eb7-109">Jeśli planujesz ujawniać typów COM innych firm do innych aplikacji, należy zawsze używać podstawowego zestawu międzyoperacyjnego pochodzącymi od tego samego wydawcy jako biblioteki typów, który definiuje.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-109">If you plan to expose third-party COM types to other applications, always use the primary interop assembly provided by the same publisher as the type library it defines.</span></span> <span data-ttu-id="f6eb7-110">Oprócz zapewnienia zgodności typu gwarantowane, podstawowe zestawy międzyoperacyjne często są dostosowane przez dostawcę do ulepszenia współdziałania.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-110">In addition to providing guaranteed type compatibility, primary interop assemblies are often customized by the vendor to enhance interoperability.</span></span>  
  
 <span data-ttu-id="f6eb7-111">Nawet jeśli nie zamierzasz ujawniać typów COM innych firm, przy użyciu podstawowego zestawu międzyoperacyjnego może ułatwić zadanie współdziałanie z COM — składniki.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-111">Even if you do not plan to expose third-party COM types, using the primary interop assembly can ease the task of interoperating with COM components.</span></span> <span data-ttu-id="f6eb7-112">Niemniej jednak ta strategia zawiera nie izolacji od zmiany, jakie typy zdefiniowane w podstawowy zestaw międzyoperacyjny wprowadzać dostawcy.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-112">However, this strategy provides no insulation from changes a vendor might make to types defined in a primary interop assembly.</span></span> <span data-ttu-id="f6eb7-113">Jeśli aplikacja wymaga takich izolacji, generowanie własnego zestawu międzyoperacyjnego zamiast podstawowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-113">When your application requires such insulation, generate your own interop assembly instead of using the primary interop assembly.</span></span>  
  
 <span data-ttu-id="f6eb7-114">Zarejestruj wszystkie nabywane podstawowe zestawy międzyoperacyjne na komputerze deweloperskim przed można odwoływać się je za pomocą [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f6eb7-114">You must register all acquired primary interop assemblies on your development computer before you can reference them with [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)].</span></span> <span data-ttu-id="f6eb7-115">Visual Studio wyszukuje i używa podstawowego zestawu międzyoperacyjnego odwołania typu z biblioteki typów COM po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-115">Visual Studio looks for and uses a primary interop assembly the first time that you reference a type from a COM type library.</span></span> <span data-ttu-id="f6eb7-116">Jeśli program Visual Studio nie może zlokalizować podstawowego zestawu międzyoperacyjnego skojarzone z biblioteki typów, wyświetli monit o jego nabycie lub oferuje zamiast tego utwórz zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-116">If Visual Studio cannot locate the primary interop assembly associated with the type library, it prompts you to acquire it or offers to create an interop assembly instead.</span></span> <span data-ttu-id="f6eb7-117">Podobnie [Importer biblioteki typów (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) używa również rejestru można znaleźć podstawowe zestawy międzyoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-117">Likewise, the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) also uses the registry to locate primary interop assemblies.</span></span>  
  
 <span data-ttu-id="f6eb7-118">Chociaż nie jest konieczne rejestrowanie podstawowych zestawów międzyoperacyjnych, chyba że planujesz używać programu Visual Studio, rejestracja dwie zalety:</span><span class="sxs-lookup"><span data-stu-id="f6eb7-118">Although it is not necessary to register primary interop assemblies unless you plan to use Visual Studio, registration provides two advantages:</span></span>  
  
-   <span data-ttu-id="f6eb7-119">Zarejestrowany podstawowy zestaw międzyoperacyjny jest jednoznacznie oznaczony w kluczu rejestru oryginalnej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-119">A registered primary interop assembly is clearly marked under the registry key of the original type library.</span></span> <span data-ttu-id="f6eb7-120">Rejestracja to najlepszy sposób można zlokalizować podstawowego zestawu międzyoperacyjnego na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-120">Registration is the best way for you to locate a primary interop assembly on your computer.</span></span>  
  
-   <span data-ttu-id="f6eb7-121">Można uniknąć przypadkowego Generowanie i przy użyciu nowego zestawu międzyoperacyjnego, jeśli w czasie w przyszłości, za pomocą programu Visual Studio odwoływać się do typu, dla którego masz wyrejestrować podstawowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-121">You can avoid accidentally generating and using a new interop assembly if, at some time in the future, you do use Visual Studio to reference a type for which you have an unregistered primary interop assembly.</span></span>  
  
 <span data-ttu-id="f6eb7-122">Użyj [narzędzie rejestracji zestawów (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) zarejestrować podstawowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-122">Use the [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) to register a primary interop assembly.</span></span>  
  
### <a name="to-register-a-primary-interop-assembly"></a><span data-ttu-id="f6eb7-123">Aby zarejestrować podstawowy zestaw międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="f6eb7-123">To register a primary interop assembly</span></span>  
  
1.  <span data-ttu-id="f6eb7-124">W wierszu polecenia wpisz polecenie:</span><span class="sxs-lookup"><span data-stu-id="f6eb7-124">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="f6eb7-125">**polecenie regasm** *assemblyname*</span><span class="sxs-lookup"><span data-stu-id="f6eb7-125">**regasm** *assemblyname*</span></span>  
  
     <span data-ttu-id="f6eb7-126">W tym poleceniu *assemblyname* to nazwa pliku zestawu, który jest zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-126">In this command, *assemblyname* is the file name of the assembly that is registered.</span></span> <span data-ttu-id="f6eb7-127">Regasm.exe dodaje wpis dla podstawowego zestawu międzyoperacyjnego w kluczu rejestru jako oryginalnego biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-127">Regasm.exe adds an entry for the primary interop assembly under the same registry key as the original type library.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6eb7-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6eb7-128">Example</span></span>  
 <span data-ttu-id="f6eb7-129">Poniższy przykład rejestruje `CompanyA.UtilLib.dll` podstawowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f6eb7-129">The following example registers the `CompanyA.UtilLib.dll` primary interop assembly.</span></span>  
  
```  
regasm CompanyA.UtilLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6eb7-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6eb7-130">See Also</span></span>  
 [<span data-ttu-id="f6eb7-131">Programowanie za pomocą podstawowe zestawy międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="f6eb7-131">Programming with Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e)  
 [<span data-ttu-id="f6eb7-132">Lokalizowanie podstawowe zestawy międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="f6eb7-132">Locating Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/d6768e4b-cd80-414d-a4f8-05d979eb393b)  
 [<span data-ttu-id="f6eb7-133">Redystrybuowanie podstawowe zestawy międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="f6eb7-133">Redistributing Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/e76384f0-d631-474c-bdbd-13884cba0265)
