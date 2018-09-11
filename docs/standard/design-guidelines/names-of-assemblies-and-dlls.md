---
title: Nazwy zestawów i bibliotek DLL
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
ms.openlocfilehash: 97bd152cff53fb1c2edb107b6d6b34bd91ca1c49
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44366950"
---
# <a name="names-of-assemblies-and-dlls"></a><span data-ttu-id="1e0b5-102">Nazwy zestawów i bibliotek DLL</span><span class="sxs-lookup"><span data-stu-id="1e0b5-102">Names of Assemblies and DLLs</span></span>
<span data-ttu-id="1e0b5-103">Zestaw jest jednostką wdrożenia i tożsamości dla programów kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-103">An assembly is the unit of deployment and identity for managed code programs.</span></span> <span data-ttu-id="1e0b5-104">Mimo że zestawy może obejmować jeden lub więcej plików, zwykle zestawu mapuje jeden do jednego z biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-104">Although assemblies can span one or more files, typically an assembly maps one-to-one with a DLL.</span></span> <span data-ttu-id="1e0b5-105">W związku z tym w tej sekcji opisano tylko DLL konwencje nazewnictwa, które następnie mogą zostać zmapowane do konwencji nazewnictwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-105">Therefore, this section describes only DLL naming conventions, which then can be mapped to assembly naming conventions.</span></span>  
  
 <span data-ttu-id="1e0b5-106">**✓ DO** wybierz nazw dla Twojego zestawu bibliotek DLL, które sugeruje duże zestawy funkcji, takich jak dane systemowe.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-106">**✓ DO** choose names for your assembly DLLs that suggest large chunks of functionality, such as System.Data.</span></span>  
  
 <span data-ttu-id="1e0b5-107">Nazwy zestawów i biblioteki DLL nie muszą odpowiadać na nazwy przestrzeni nazw, ale jest postępuj zgodnie z nazwą przestrzeni nazw podczas nadawania nazw zestawów.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-107">Assembly and DLL names don’t have to correspond to namespace names, but it is reasonable to follow the namespace name when naming assemblies.</span></span> <span data-ttu-id="1e0b5-108">Regułą jest nazwa biblioteki DLL, w oparciu o Wspólny prefiks przestrzeni nazw są zawarte w zestawie.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-108">A good rule of thumb is to name the DLL based on the common prefix of the namespaces contained in the assembly.</span></span> <span data-ttu-id="1e0b5-109">Na przykład zestaw o dwie przestrzenie nazw, `MyCompany.MyTechnology.FirstFeature` i `MyCompany.MyTechnology.SecondFeature`, może być wywoływana `MyCompany.MyTechnology.dll`.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-109">For example, an assembly with two namespaces, `MyCompany.MyTechnology.FirstFeature` and `MyCompany.MyTechnology.SecondFeature`, could be called `MyCompany.MyTechnology.dll`.</span></span>  
  
 <span data-ttu-id="1e0b5-110">**✓ CONSIDER** nazewnictwa bibliotek DLL według następującego wzorca:</span><span class="sxs-lookup"><span data-stu-id="1e0b5-110">**✓ CONSIDER** naming DLLs according to the following pattern:</span></span>  
  
 `<Company>.<Component>.dll`  
  
 <span data-ttu-id="1e0b5-111">gdzie `<Component>` zawiera jedną lub więcej klauzul oddzielone kropką.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-111">where `<Component>` contains one or more dot-separated clauses.</span></span> <span data-ttu-id="1e0b5-112">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1e0b5-112">For example:</span></span>  
  
 <span data-ttu-id="1e0b5-113">`Litware.Controls.dll`.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-113">`Litware.Controls.dll`.</span></span>  
  
 <span data-ttu-id="1e0b5-114">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="1e0b5-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1e0b5-115">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="1e0b5-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e0b5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e0b5-116">See also</span></span>

- [<span data-ttu-id="1e0b5-117">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="1e0b5-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="1e0b5-118">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="1e0b5-118">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
