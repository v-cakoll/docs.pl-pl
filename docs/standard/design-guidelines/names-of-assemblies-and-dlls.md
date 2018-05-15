---
title: Nazw zestawów i bibliotek DLL
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6cf175472d68e99598dd56e170bee3d37ae3c2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="a3b95-102">Nazw zestawów i bibliotek DLL</span><span class="sxs-lookup"><span data-stu-id="a3b95-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="a3b95-103">Zestaw jest jednostką wdrożenia i tożsamości dla programów kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a3b95-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="a3b95-104">Mimo że zestawy mogą znajdować się co najmniej jednego pliku, zwykle zestawu mapuje jeden do jednego z biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="a3b95-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="a3b95-105">W związku z tym w tej sekcji opisano tylko DLL konwencji nazewnictwa, które następnie mogą być mapowane na zestawie konwencji nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="a3b95-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="a3b95-106">**CZY ✓** wybierz nazw dla Twojego zestawu bibliotek DLL, które sugeruje duże zestawy funkcji, takich jak dane systemowe.</span><span class="sxs-lookup"><span data-stu-id="a3b95-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="a3b95-107">Nazwa pliku zestawu i biblioteki DLL nie musi odpowiadać nazwy przestrzeni nazw, ale można wykonać nazwę przestrzeni nazw w nazwach zestawów.</span><span class="sxs-lookup"><span data-stu-id="a3b95-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="a3b95-108">Regułą jest nazwa biblioteki DLL, na podstawie prefiksu wspólnej przestrzeni nazw zawartych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="a3b95-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="a3b95-109">Na przykład zestaw o dwie przestrzenie nazw, `MyCompany.MyTechnology.FirstFeature` i `MyCompany.MyTechnology.SecondFeature`, może być wywoływana `MyCompany.MyTechnology.dll`.</span><span class="sxs-lookup"><span data-stu-id="a3b95-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="a3b95-110">**ROZWAŻ ✓** nazewnictwa bibliotek DLL według następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="a3b95-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="a3b95-111">gdzie `<Component>` zawiera co najmniej jedną klauzulę oddzielona kropkami.</span><span class="sxs-lookup"><span data-stu-id="a3b95-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="a3b95-112">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a3b95-112">For example:</span></span>  
  
 <span data-ttu-id="a3b95-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="a3b95-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="a3b95-114">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="a3b95-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a3b95-115">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="a3b95-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b95-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3b95-116">See Also</span></span>  
 [<span data-ttu-id="a3b95-117">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="a3b95-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="a3b95-118">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="a3b95-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
